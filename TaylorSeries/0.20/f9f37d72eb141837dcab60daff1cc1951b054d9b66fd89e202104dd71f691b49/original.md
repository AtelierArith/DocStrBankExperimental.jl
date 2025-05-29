```
Taylor1{T<:Number} <: AbstractSeries{T}
```

DataType for polynomial expansions in one independent variable.

**Fields:**

  * `coeffs :: Array{T,1}` Expansion coefficients; the $i$-th   component is the coefficient of degree $i-1$ of the expansion.
  * `order  :: Int` Maximum order (degree) of the polynomial.

Note that `Taylor1` variables are callable. For more information, see [`evaluate`](@ref).
