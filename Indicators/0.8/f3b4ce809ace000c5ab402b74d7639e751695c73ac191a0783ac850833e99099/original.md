```
diffn(x::Vector{T}; n::Int=1)::Vector{T} where {T<:Real}
diffn(X::Matrix; n::Int=1)::Matrix = hcat([diffn(X[:,j], n=n) for j in 1:size(X,2)]...)
```

Lagged differencing
