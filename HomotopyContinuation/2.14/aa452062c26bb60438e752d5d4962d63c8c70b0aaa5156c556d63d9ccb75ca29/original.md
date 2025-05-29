```
add!(unique_points, v, id; atol = 1e-14, rtol = sqrt(eps()))
add!(unique_points, v, id, atol)
```

Search whether `unique_points` contains a point `p` with distances at most `max(atol, norm(v)rtol)` from `v`. If this is the case the identifier of `p` and `false` is returned. Otherwise `(id, true)` is returned.
