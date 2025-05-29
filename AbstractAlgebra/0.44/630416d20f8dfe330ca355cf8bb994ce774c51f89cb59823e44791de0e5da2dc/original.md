```
remove(z::MPolyRingElem{T}, p::MPolyRingElem{T}) where {T <: RingElement}
```

Compute the valuation of $z$ at $p$, that is, the largest $k$ such that $p^k$ divides $z$. Additionally, $z/p^k$ is returned as the second return. value.

See also `valuation`, which only returns the valuation.
