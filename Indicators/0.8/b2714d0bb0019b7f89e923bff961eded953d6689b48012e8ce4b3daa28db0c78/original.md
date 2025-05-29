```
runcov(x::Vector{T}, y::Vector{T}; n::Int=10, cumulative::Bool=true)::Vector{Float64}
runcov(X::Matrix, Y::Matrix; n::Int=10, cumulative::Bool=true)::Matrix{Float64}
```

Compute the running or rolling covariance of two arrays
