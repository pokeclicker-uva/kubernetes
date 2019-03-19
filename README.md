# PokéClicker Kubernetes
The k8s files for PokéClicker

## Deployment
To deploy these applications onto a k8s cluster, you first have to create the namespace:
```sh
kubectl create -f ./pokeclicker/namespace.yaml
```

The next is to create the necessary secrets. Place each of them in a file without
a file extension in the root of directory and name them accordingly to the following command and execute it:
```sh
kubectl -n=pokeclicker create secret generic backend --from-file ./db_username --from-file ./db_password --from-file ./db_root_password --from-file ./sentry_dsn
```

Finally, deploy the actual applications:
```sh
kubectl create -R -f ./pokeclicker/applications/
```

You can check if the deployment succeeded with a look over the deployed pods:
```sh
kubectl get pods
```
