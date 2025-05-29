```
empirical_emd(x::Union{PyObject, Array{Float64}}, y::Union{PyObject, Array{Float64}};
    iter::Int64 = 1000, tol::Float64 = 1e-9, dist::Union{Integer,Function}=2, returnall::Bool=false)
```

[`empirical_sinkhorn`](@ref) と同様ですが、地球移動者距離が計算されます。
