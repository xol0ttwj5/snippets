# Kubectl Debug Snippets

Quick commands for common pod troubleshooting.

## Pod stuck in Pending

```bash
kubectl describe pod <pod> -n <ns>
kubectl get events --sort-by=.lastTimestamp -n <ns> | tail -20
```

## CrashLoopBackOff

```bash
kubectl logs <pod> --previous -n <ns>
kubectl get pod <pod> -o yaml -n <ns> | grep -A10 lastState
```

## Node NotReady

```bash
kubectl get nodes -o wide
kubectl describe node <node> | grep -A5 Conditions
```

## Container image pull failure

```bash
kubectl describe pod <pod> -n <ns> | grep -i events -A5
```