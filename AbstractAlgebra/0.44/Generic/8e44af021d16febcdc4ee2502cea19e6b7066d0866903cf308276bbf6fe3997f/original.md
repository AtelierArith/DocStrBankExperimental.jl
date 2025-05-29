```
valuation(a::LocalizedEuclideanRingElem{T}, p::T) where {T <: RingElement}
```

Returns the valuation `n` of $a$ at $p$, i.e. the integer `n` s.th $a$ = $p$^`n` * x, where x has valuation 0 at $p$.
