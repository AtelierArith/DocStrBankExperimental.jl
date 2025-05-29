```
getinterpolRing(resol::Resolution, θ, ϕ) -> (Array{Int,1}, Array{Float64, 1})
getinterpolRing!(resol::Resolution, θ, ϕ, pix, weights) -> (Array{Int,1}, Array{Float64, 1})
```

Return the indices and the weights of the four neighbour pixels for the given direction (θ, ϕ) in a map with the specified resolution.

If provided, the parameters `pix` and `weights` should point to two 4-element arrays of integers and floating-points, respectively. They can be reused in multiple calls to avoid heap allocations and speed up the code.
