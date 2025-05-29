```
radon(u:Vector, v:Vector, ϕ:RealU, θ:RealU, oa::Array{<:Object3d})
```

Return parallel-beam projection view sampled at grid of `(u,v)` locations for a given `(ϕ,θ)` pair. Returned array size is `length(u) × length(v)`.
