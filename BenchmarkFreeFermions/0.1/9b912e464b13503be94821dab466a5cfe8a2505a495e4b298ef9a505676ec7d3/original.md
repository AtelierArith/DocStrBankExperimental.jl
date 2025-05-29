```
 TimeCorrelation(ξ::Vector{Float64},
      V::Matrix,
      β::Real,
      si::Vector{Int64},
      dagidx::Vector{Int64},
      lsτ::AbstractVector{<:Number}) -> ::Float64(::ComplexF64)
```

Return the time correlation function with the shifted single particle spectrum `ξ = ϵ - μ` and the eigenvectors `V` obtained from `Tij = - V diagm(ϵ) V'`. `si` denotes the sites and `dagidx` tells whether the operator is daggered or not. `lsτ` has the same length as `si` and tells the time of each operator. For example, `si = [i, j, k, l]`, `dagidx = [1, 3]` and `lsτ = [τ1, τ2, 0, 0]` means `c_i^dag(τ1) c_j(τ2) c_k^dag c_l`.   
