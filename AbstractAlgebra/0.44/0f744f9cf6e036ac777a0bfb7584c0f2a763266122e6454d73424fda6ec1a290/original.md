```
interpolate(S::PolyRing, x::Vector{T}, y::Vector{T}) where T <: RingElement
```

Given two arrays of values $xs$ and $ys$ of the same length $n$, find the polynomial $f$ in the polynomial ring $R$ of length at most $n$ such that $f$ has the value $ys$ at the points $xs$. The values in the arrays $xs$ and $ys$ must belong to the base ring of the polynomial ring $R$. If no such polynomial exists, an exception is raised.
