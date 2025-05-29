```
Blackbox{T, U}(ω::Vector{Float64}, Y::Vector{U}, P::U, Q::U,
    ports::UniqueVector{T}) where {T, U}
Blackbox(ω::Vector{<:Real}, Y::Vector{U}, P::U, Q::U,
    ports::AbstractVector{T}) where {T, U}
```

An admittance model with constant `P` and `Q` but with varying `Y`, indexed by a real variable `ω`.
