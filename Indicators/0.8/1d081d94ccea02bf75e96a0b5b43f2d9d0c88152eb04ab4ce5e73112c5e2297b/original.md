```
ichimoku(hlc::AbstractMatrix{T}; params=(9, 26, 26, 52, -26))::Matrix{Float64} where {T<:Real}
```

Ichimoku Kinko Hyo

*Output*

  * Column 1: Tenkan-sen
  * Column 2: Kijun-sen
  * Column 3: Senkou Span A
  * Column 4: Senkou Span B
  * Column 5: Chikou Span
