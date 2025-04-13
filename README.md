## Setup

1. install vcluster cli
```
brew install loft-sh/tap/vcluster
```

1. Deploy vcluster without ingress, without connecting to it
```
vcluster create team-a -n team-a --connect=false --values vcluster_values.yaml
```

1. save the kubeconfig file of the newly created vcluster
```
 vcluster connect team-a -n team-a --print > team-a-kubconfig.yaml
```

1. connect to the new vcluster in a separate terminal
```
export KUBECONFIG=./team-a-kubconfig.yaml
```

1. deploy a test application (from the vcluster)

```
kubectl apply -f silly-app
```

1. Update /etc/hosts
```
127.0.0.1 mycompany.com silly-app.team-a.mycompany.com
```

1. Pause vcluster (from the host cluster)
```
vcluster pause team-a -n team-a
```

1. Resume vcluster (from the host cluster)
```
vcluster resume team-a -n team-a
```