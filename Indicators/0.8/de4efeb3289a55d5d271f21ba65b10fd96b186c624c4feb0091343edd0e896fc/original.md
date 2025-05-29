```
bbands(x::Array{T}; n::Int64=10, sigma::T=2.0)::Matrix{Float64}
```

Bollinger bands (moving average with standard deviation bands)

*Output*

  * Column 1: lower band
  * Column 2: middle band
  * Column 3: upper band
