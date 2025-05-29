```
is_vector(M::Segre{ℝ, V}, p, X, kwargs...)
```

Check whether `X` is a tangent vector to `p` on `M`, i.e. `X` has to be of same dimension as `p` and orthogonal to `p`. The tolerance can be set using the `kwargs...`.
