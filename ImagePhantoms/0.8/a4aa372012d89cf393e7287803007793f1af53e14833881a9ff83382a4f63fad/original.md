```
radon(r::Vector, ϕ::Vector, oa::Array{<:Object2d})
```

Return parallel-beam 2D sinogram sampled at grid of `(r,ϕ)` locations. Returned array size is `length(r) × length(ϕ)`.
