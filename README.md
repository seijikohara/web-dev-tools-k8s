# Kubernetes manifest for [web-dev-tools](https://github.com/seijikohara/web-dev-tools)

## Refs

- https://spring.pleiades.io/guides/topicals/spring-on-kubernetes/

```shell
# Create manifest file
kubectl create deployment web-dev-tools --image seijikohara/web-dev-tools -o yaml --dry-run=client > deployment.yaml
kubectl create service clusterip web-dev-tools --tcp 80:20000 -o yaml --dry-run=client > service.yaml

# Apply manifest file
kubectl apply -f ./

# Port forwarding
kubectl port-forward svc/web-dev-tools 9090:80

# Create ConfigMap
kubectl create configmap web-dev-tools --from-file=application.properties
kubectl get configmap web-dev-tools -o yaml
```