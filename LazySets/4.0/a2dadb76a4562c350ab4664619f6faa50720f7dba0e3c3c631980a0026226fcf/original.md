# Extended help

```
norm(X::LazySet, [p]::Real=Inf)
```

### Algorithm

The default implementation handles the case `p == Inf` using `extrema`. Otherwise it checks whether `X` is polytopic, in which case it iterates over all vertices.
