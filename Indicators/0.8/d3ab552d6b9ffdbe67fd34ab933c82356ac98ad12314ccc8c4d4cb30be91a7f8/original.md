```
runmean(x::Array{T}; n::Int=10, cumulative::Bool=true)::Array{T}
runmean(X::Matrix; n::Int=10, cumulative::Bool=true)::Matrix{Float64}
```

Compute a running or rolling arithmetic mean of an array.
