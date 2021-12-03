# awx setup in kubernetes using awx operator

# Pre-requisite

makesure you have kubernetes cluster running with atleast 4 cpus & 6GB ram.

# Deploying awx operator, postgres, awx

**awx operator installation**

kubectl apply -f awx-resources.yaml

**Note**: the above command creates `awx` namespace and deploys awx operator in `awx` namespace. Ensure that pod is running state prior proceeding.

**changing the context**

Lets change the context to `awx` namespace by executing the below command.

kubectl config set-context --current --namespace=awx

**Deploying awx instance**

kubectl apply -f awx-demo.yaml

The above command deploys `postgres` & `awx` instance. This will take some time. So please wait.
Makesure that all the pods are in running state.

# Accessing awx webui

there is service named `awx-demo-service` deployed. Execute `kubectl port-forward` against this service.

Go to the browser & open the endpoint

username: admin
password can be found at `kubectl get secret awx-demo-admin-password -o jsonpath="{.data.password}" | base64 --decode`



