```
macd(x::Array{T}; nfast::Int64=12, nslow::Int64=26, nsig::Int64=9)::Array{Float64}
```

Moving average convergence-divergence

*Output*

  * Column 1: MACD
  * Column 2: MACD Signal Line
  * Column 3: MACD Histogram
