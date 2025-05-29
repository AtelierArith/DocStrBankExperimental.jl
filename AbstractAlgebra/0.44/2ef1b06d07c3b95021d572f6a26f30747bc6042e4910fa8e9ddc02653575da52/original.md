```
valuation(z::MPolyRingElem{T}, p::MPolyRingElem{T}) where {T <: RingElement}
```

Compute the valuation of $z$ at $p$, that is, the largest $k$ such that $p^k$ divides $z$.

See also `remove`, which also returns $z/p^k$.
