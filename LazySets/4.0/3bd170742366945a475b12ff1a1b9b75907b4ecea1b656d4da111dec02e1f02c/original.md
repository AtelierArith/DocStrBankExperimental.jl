# Extended help

```
⊂(X::LazySet, Y::LazySet, [witness]::Bool=false)
```

### Algorithm

The default implementation first checks inclusion of `X` in `Y` and then checks noninclusion of `Y` in `X`:
