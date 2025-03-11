In a Minikube cluster we can install Apisix using a Helm Chart

```
helm repo add apisix https://charts.apiseven.com \
    && helm repo update \
    && helm upgrade \
    --install apisix apisix/apisix \
    --create-namespace  --namespace apisix \
    --set dashboard.enabled=true \
    --set ingress-controller.enabled=true \
    --set ingress-controller.config.apisix.serviceNamespace=apisix
```

There will be some issues during installation. The way I found to solve it is to delete the ingress-controller pod and then delete the dashboard pod until I see all the pods healthy

After we have apisix up and running, we can install Keycloak

```
kubectl apply -f keycloak.yaml
```
