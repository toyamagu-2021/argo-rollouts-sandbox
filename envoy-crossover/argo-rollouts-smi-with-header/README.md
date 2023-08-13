# Argo Rollouts with envoy crossover

## Description

Pure envoy with crossover traffic weight.

- RDS: Route Discovery Service

## Procedure

- `kind create cluster`
- `helmfile sync .`
- Test 50/50

```bash
kubectl run -it --rm --image alpine tester sh

apk add --update curl
watch curl http://envoy:10000
watch curl -H 'x-user:test' http://envoy:10000
```

- Test other weight
  - Edit `./values-envoy/values-services.yaml`

## References

- [crossover]: https://github.com/mumoshu/crossover
