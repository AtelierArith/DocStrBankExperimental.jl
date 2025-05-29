```
derivative(f, x, ::Val{P})
derivative(f, x, l, ::Val{P})
derivative(f!, y, x, l, ::Val{P})
```

Computes `P`-th directional derivative of `f` w.r.t. vector `x` in direction `l`. If `x` is a Number, the direction `l` can be omitted.
