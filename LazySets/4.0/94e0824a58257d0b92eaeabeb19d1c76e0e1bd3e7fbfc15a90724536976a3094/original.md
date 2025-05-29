# Extended help

```
rectify(X::LazySet, [concrete_intersection]::Bool=false)
```

### Algorithm

For each dimension in which `X` is both positive and negative, we split `X` into these two parts and then project the negative part to zero.
