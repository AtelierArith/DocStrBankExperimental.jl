```
is_point(M::Segre{ℝ, V}, p; kwargs...)
```

Check whether `p` is a valid point on `M`, i.e. `p[1]` is a singleton containing a positive number and `p[i + 1]` is a point on `Sphere(V[i])`. The tolerance can be set using the `kwargs...`.
