# **Ferramentas necessárias**
- kind | minikube | microk8s: provisionar o cluster k8s
- kubectl: linha de comando para interagir com o cluster k8s
- Helm v3: package manager do k8s
   
1. Provisionar o cluster 
    * infra/kong-k8s/kind/kind.sh

1. Instalar o kong no cluster k8s 
    * infra/kong-k8s/kong/kong.sh

# Ferramentas adicionais (pasta misc)
1. Prometheus Stack - Monitoramento (alertmanager, prometheus, grafana, operator, metrics, exporter)
    * infra/kong-k8s/misc/prometheus/prometheus.sh

2. Keycloack - Open ID Connect
    * infra/kong-k8s/misc/keycloak/keycloack.sh

3. APPs
    * Criar o namespace no cluster: kubectl create ns bets
    * kubectl apply -f infra/kong-k8s/misc/apps . --recursive -n bets

# Monitoramento do k8s
- kubectl get po -A
- watch -n 0.2 kubectl get pods -n kong
- watch -n 0.2 kubectl get pods -n monitoring
- watch -n 0.2 kubectl get pods -n iam
- watch -n 0.2 kubectl get pods -n bets

- kubectl describe pods kong-kong-5d6cc5d877-7bnbc -n kong
- kubectl logs kong-kong-5d6cc5d877-7bnbc proxy -n kong
- kubectl --namespace monitoring get pods -l "release=prometheus-stack

