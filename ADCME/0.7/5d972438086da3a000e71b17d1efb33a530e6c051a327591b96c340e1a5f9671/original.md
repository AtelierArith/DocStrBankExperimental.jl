```
empirical_emd(x::Union{PyObject, Array{Float64}}, y::Union{PyObject, Array{Float64}};
    iter::Int64 = 1000, tol::Float64 = 1e-9, dist::Union{Integer,Function}=2, returnall::Bool=false)
```

Same as [`empirical_sinkhorn`](@ref), except that the Earth Mover Distance is computed. 
