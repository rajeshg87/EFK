minikube start --memory 4096 --cpus 3

kubectl create namespace logging

kubectl apply -f elastic.yaml -n logging

kubectl apply -f kibana.yaml -n logging

kubectl get service -n logging

kubectl apply -f fluentd-rbac.yaml 

kubectl apply -f fluentd-daemonset.yaml 

kubectl apply -f logging-pod.yaml -n logging

kubectl apply -f logging-deployment.yaml -n logging

kubectl get pods -n kube-system

rm -rf ~/.minikube 

docker build -t rajeshg87/spring-logging-app:1.0 .
docker push rajeshg87/spring-logging-app:1.0

docker rmi $(docker images -q)