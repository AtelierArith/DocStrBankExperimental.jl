```
aw(x::ProductSimplex{T}) where T <: Tuple{Vararg{AbstractSimplex}} -> Linear{Tensor{T}}
```

Return the image of the given product simplex under the Alexander-Whitney map. The product simplex may have any number of components, including zero. The number of components in the resulting tensor product is the same as the number of components of the product simplex.

This function is linear and supports the keyword arguments `coefftype`, `addto`, `coeff` and `is_filtered` as described for the macro `@linear`.

See also [`coprod`](@ref), [`ez`](@ref), [`shih`](@ref), `LinearCombinations.@linear`.

# Examples

```jldoctest
julia> x, y = SymbolicSimplex(:x, 2), SymbolicSimplex(:y, 2)
(x[0,1,2], y[0,1,2])

julia> aw(ProductSimplex(x, y))
Linear{Tensor{Tuple{SymbolicSimplex{Symbol}, SymbolicSimplex{Symbol}}}, Int64} with 3 terms:
x[0]⊗y[0,1,2]+x[0,1,2]⊗y[2]+x[0,1]⊗y[1,2]

julia> z = SymbolicSimplex(:z, 2); aw(ProductSimplex(x, y, z))
Linear{Tensor{Tuple{SymbolicSimplex{Symbol}, SymbolicSimplex{Symbol}, SymbolicSimplex{Symbol}}}, Int64} with 6 terms:
x[0,1]⊗y[1]⊗z[1,2]+x[0,1,2]⊗y[2]⊗z[2]+x[0,1]⊗y[1,2]⊗z[2]+x[0]⊗y[0]⊗z[0,1,2]+x[0]⊗y[0,1]⊗z[1,2]+x[0]⊗y[0,1,2]⊗z[2]

julia> aw(ProductSimplex(x))
Linear{Tensor{Tuple{SymbolicSimplex{Symbol}}}, Int64} with 1 term:
x[0,1,2]

julia> aw(ProductSimplex(; dim = 0))
Linear{Tensor{Tuple{}}, Int64} with 1 term:
()
```
