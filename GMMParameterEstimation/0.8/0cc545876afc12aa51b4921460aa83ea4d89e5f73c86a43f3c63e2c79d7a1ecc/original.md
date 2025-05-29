```
build1DSystem(k::Integer, m::Integer, a::Union{Vector{Float64}, Vector{Variable}})
```

Build the polynomial system for a mixture of 1D Gaussians where 'm'-1 is the highest desired moment, and `a` is a vector of the mixing coefficients.
