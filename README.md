# Cloud-developer-Project : Udacity Nano degree project

Links to Docker-hub images: 
  - Feed: https://hub.docker.com/repository/docker/zakidokerid/udacity-restapi-feed
  - User: https://hub.docker.com/repository/docker/zakidokerid/udacity-restapi-user 
  - Frontend: https://hub.docker.com/repository/docker/zakidokerid/udacity-frontend 
  - ReverseProxy: https://hub.docker.com/repository/docker/zakidokerid/reverseproxy

Screenshots are located in the root of the repository.

Instructions: 
  - Build the images: 
      - docker-compose -f docker-compose-build.yaml build --parallel 
  - Push the images: 
      - docker-compose -f docker-compose-build.yaml push
    
  - Create eks cluster: 
    - eksctl create cluster   --version 1.14   --region us-east-2   --node-type t3.medium   --nodes 4   --nodes-min 1   --nodes-max 5   --name udagram

  - Apply confiMap and secrets: 
    - kubectl apply -f env-configmap.yaml
    - kubectl apply -f aws-secret.yaml
    - kubectl apply -f env-secret.yaml 

  - Apply Kubernetes deployments:
    - kubectl apply -f beckend-feed-deployment.yaml 
    - kubectl apply -f beckend-user-deployment.yaml
    - kubectl apply -f frontend-deployment.yaml
    - kubectl apply -f reverseproxy-deployment.yaml

  - Apply Kubernetes services:
    - kubectl apply -f beckend-feed-service.yaml 
    - kubectl apply -f beckend-user-service.yaml
    - kubectl apply -f frontend-service.yaml
    - kubectl apply -f reverseproxy-service.yaml
  
  - Apply port forwaring:
    - kubectl port-forward service/reverseproxy 8080:8080
    
    
