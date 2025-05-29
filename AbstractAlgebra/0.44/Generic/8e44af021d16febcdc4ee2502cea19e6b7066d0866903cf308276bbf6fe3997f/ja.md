```
valuation(a::LocalizedEuclideanRingElem{T}, p::T) where {T <: RingElement}
```

$ a $ の $ p $ における評価値 `n` を返します。すなわち、$ a $ = $ p :^`n` * x であり、ここで x は $ p $ において評価値 0 を持ちます。
