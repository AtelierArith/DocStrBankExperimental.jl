```
get_entEntropy!(rho::Matrix{T}, lambdas::AbstractVector{Float64}; tol=1E-10, check::Bool=true) where T <: Union{Float64, ComplexF64}
```

get the entanglement entropy Sv and in palce create the entanglement spectrum `lambdas`.
