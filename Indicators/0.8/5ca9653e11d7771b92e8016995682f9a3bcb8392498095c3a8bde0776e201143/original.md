```
runsum(x::Vector{T}; n::Int=10, cumulative::Bool=true)::Vector{Float64}
runsum(X::Matrix; n::Int=10, cumulative::Bool=true)::Matrix{Float64}
```

Compute a running or rolling summation of an array.
