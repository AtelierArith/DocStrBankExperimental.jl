```
function QuadratureRule{T,ET}(order::Int) where {T<:Real, ET <: AbstractElementGeometry0D}
```

Constructs 0D quadrature rule of specified order (always point evaluation).
