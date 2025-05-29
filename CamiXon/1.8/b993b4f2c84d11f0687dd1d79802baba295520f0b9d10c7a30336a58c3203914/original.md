```
getΔNcut(f0::T, f::Vector{T}, Ncut::Int, sense=fwd; ϵ = 1e-8, k = 7)
```

Offset of the exact intersection with respect to the index `Ncut` given as a Real number. `ϵ` - convergence goal `k` - order of a k+1 point Lagrange interpolation procedure based on a *linear* grid.  Forward sense (`fwd`): value in the interval {0.0, 1.0} Backward sense (`bwd`): value in the interval {-1.0, 0.0}
