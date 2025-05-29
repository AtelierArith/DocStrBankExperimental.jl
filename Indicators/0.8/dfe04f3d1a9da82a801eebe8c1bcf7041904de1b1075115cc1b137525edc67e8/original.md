```
function runacf(x::Vector{T};
                n::Int = 10,
                maxlag::Int = n-3,
                lags::AbstractVector{Int,1} = 0:maxlag,
                cumulative::Bool = true)::Matrix{T} where {T<:Real}
                runacf(X::Matrix; n::Int=10, cumulative::Bool=true, maxlag::Int=n-3, lags::AbstractVector{Int}=0:maxlag)::Matrix{Float64}
```

Compute the running/rolling autocorrelation of a vector.
