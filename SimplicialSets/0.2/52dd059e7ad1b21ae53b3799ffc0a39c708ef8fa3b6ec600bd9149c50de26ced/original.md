```
diag(x::T) where T <: AbstractSimplex -> ProductSimplex{Tuple{T,T}}
```

Return the image of `x` under the diagonal map from the simplicial set containing `x` to the Cartesian product with itself.

This function is linear and supports the keyword arguments `coefftype`, `addto`, `coeff`, `sizehint` and `is_filtered` as described for the macro `@linear`.

See also [`coprod`](@ref), `LinearCombinations.@linear`.
