```
runmax(x::Vector{T}; n::Int=10, cumulative::Bool=true, inclusive::Bool=true)::Vector{Float64}
runmax(X::Matrix; n::Int=10, cumulative::Bool=true, inclusive::Bool=true)::Matrix{Float64}
```

Compute the running or rolling maximum of an array
