```
TaylorN{T<:Number} <: AbstractSeries{T}
```

DataType for polynomial expansions in many (>1) independent variables.

**Fields:**

  * `coeffs  :: Array{HomogeneousPolynomial{T},1}` Vector containing the

`HomogeneousPolynomial` entries. The $i$-th component corresponds to the homogeneous polynomial of degree $i-1$.

  * `order   :: Int`  maximum order of the polynomial expansion.

Note that `TaylorN` variables are callable. For more information, see [`evaluate`](@ref).
