```
runmad(x::Vector{T}; n::Int=10, cumulative::Bool=true, fun::Function=median)::Vector{Float64}
runmad(X::Matrix; n::Int=10, cumulative::Bool=true)::Matrix{Float64}
```

Compute the running or rolling mean absolute deviation of an array
