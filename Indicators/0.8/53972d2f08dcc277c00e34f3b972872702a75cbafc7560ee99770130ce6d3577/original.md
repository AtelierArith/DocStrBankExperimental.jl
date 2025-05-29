```
mlr_bands(y::Array{T}; n::Int64=10, se::T=2.0)::Matrix{Float64} where {T<:Real}
```

Moving linear regression bands

*Output:*

Column 1: Lower bound

Column 2: Regression estimate

Column 3: Upper bound
