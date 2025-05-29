```
post_crush(pr::PresolveResult{T}, x::Vector{T}; is_ray::Bool=false)
```

Map a point from the presolved model to the original model. If `is_ray = false`, the point should be a feasible point for the presolved model; otherwise, it should be an unbounded ray.

Note: Throws an error if the length of `x` is not equal to the number of variables in the presolved model.
