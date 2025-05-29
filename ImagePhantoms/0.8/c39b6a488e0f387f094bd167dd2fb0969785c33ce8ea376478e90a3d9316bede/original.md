```
radon(u:Vector, v:Vector, ϕ:Vector, θ:Vector, oa::Array{<:Object3d})
```

Return parallel-beam projections sampled at grid of `(u,v,ϕ,θ)` locations. Returned array size is `length(u) × length(v) × length(ϕ) × length(θ)`.
