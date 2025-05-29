```
HomogeneousPolynomial{T<:Number} <: AbstractSeries{T}
```

DataType for homogeneous polynomials in many (>1) independent variables.

**Fields:**

  * `coeffs  :: Array{T,1}` Expansion coefficients of the homogeneous

polynomial; the $i$-th component is related to a monomial, where the degrees of the independent variables are specified by `coeff_table[order+1][i]`.

  * `order   :: Int` order (degree) of the homogeneous polynomial.

Note that `HomogeneousPolynomial` variables are callable. For more information, see [`evaluate`](@ref).
