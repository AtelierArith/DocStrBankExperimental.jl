Renko chart patterns

# Methods

```
function renko(x::Array{T}; box_size::T=10.0)::Array{Int} where {T<:Real}

function renko(hlc::Matrix{T}; box_size::T=10.0, use_atr::Bool=false, n::Int=14)::Array{Int} where {T<:Real}
```

  * Traditional (Constant Box Size): `renko(x::Array{T}; box_size::T=10.0)::Array{Int}`
  * ATR Dynamic Box Size: `renko(hlc::Matrix{T}; box_size::T=10.0, use_atr::Bool=false, n::Int=14)::Array{Int}`

# Output

`Array{Int}` object of size Nx1 (where N is the number rows in `x`) where each element gives the Renko bar number of the corresponding row in `x`.
