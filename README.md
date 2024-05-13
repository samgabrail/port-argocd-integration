# Overview
Integrate Port with ArgoCD

## Guides Used
- https://docs.getport.io/guides-and-tutorials/visualize-service-argocd-runtime/?deploy=helm
- https://docs.getport.io/create-self-service-experiences/setup-backend/github-workflow/examples/argocd/sync-argocd-app/

## Install the Integration
The following script will install an Ocean integration in your K8s cluster using helm
```bash
helm repo add --force-update port-labs https://port-labs.github.io/helm-charts
helm upgrade --install argocd port-labs/port-ocean \
	--set port.clientId="YOUR_PORT_CLIENT_ID"  \
	--set port.clientSecret="YOUR_PORT_CLIENT_SECRET"  \
	--set port.baseUrl="https://api.getport.io"  \
	--set initializePortResources=true  \
	--set integration.identifier="argocd"  \
	--set integration.type="argocd"  \
	--set integration.eventListener.type="POLLING"  \
	--set integration.secrets.token="YOUR_ARGOCD_TOKEN"  \
	--set integration.config.serverUrl="YOUR_ARGOCD_SERVER_URL" 
```

