# Extended help

```
isuniversal(S::LazySets.AbstractCentrallySymmetric, [witness]::Bool=false)
```

### Algorithm

A witness is obtained by computing the support vector in direction `d = [1, 0, …, 0]` and adding `d` on top.
