1) kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
2) apply ingress
3) disable TLS - kubectl -n argocd edit deployment.apps argocd-server
    ...
    containers:
    - command:
      - argocd-server
      - --insecure
      - --staticassets
      - /shared/app
    ...
4) get admin pass - kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
