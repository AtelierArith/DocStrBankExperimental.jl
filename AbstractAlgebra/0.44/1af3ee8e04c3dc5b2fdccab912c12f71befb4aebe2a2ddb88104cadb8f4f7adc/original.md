```
derivative(f::MPolyRingElem{T}, x::MPolyRingElem{T}) where T <: RingElement
```

Return the partial derivative of `f` with respect to `x`. The value `x` must be a generator of the polynomial ring of `f`.
