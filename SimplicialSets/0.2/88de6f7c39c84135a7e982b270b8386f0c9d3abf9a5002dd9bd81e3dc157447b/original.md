```
shih(z::ProductSimplex{T}) where T <: Tuple{AbstractSimplex,AbstractSimplex} -> Linear{T}
shih_eml(z::ProductSimplex{T}) where T <: Tuple{AbstractSimplex,AbstractSimplex} -> Linear{T}
```

Return the image of the product simplex `z` under the Eilenberg–MacLane homotopy (which is sometimes called the Shih map).

This function is linear and supports the keyword arguments `coefftype`, `addto`, `coeff`, `sizehint` and `is_filtered` as described for the macro `@linear`.

See also [`aw`](@ref), [`ez`](@ref), [`shih_opp`](@ref), `LinearCombinations.@linear`.

# Examples

```jldoctest
julia> x, y = SymbolicSimplex(:x, 2), SymbolicSimplex(:y, 2); z = ProductSimplex(x, y)
(x[0,1,2],y[0,1,2])

julia> shih(z)
Linear{ProductSimplex{Tuple{SymbolicSimplex{Symbol}, SymbolicSimplex{Symbol}}}, Int64} with 4 terms:
-(x[0,1,1,2],y[0,1,2,2])+(x[0,0,1,1],y[0,1,1,2])-(x[0,0,0,1],y[0,1,2,2])+(x[0,0,1,2],y[0,2,2,2])

julia> shih(ez(x, y))
Linear{ProductSimplex{Tuple{SymbolicSimplex{Symbol}, SymbolicSimplex{Symbol}}}, Int64} with 0 terms:
0

julia> shih(ez(x, y))
Linear{ProductSimplex{Tuple{SymbolicSimplex{Symbol}, SymbolicSimplex{Symbol}}}, Int64} with 0 terms:
0

julia> aw(shih(z))
Linear{Tensor{Tuple{SymbolicSimplex{Symbol}, SymbolicSimplex{Symbol}}}, Int64} with 0 terms:
0

julia> shih(shih(z))
Linear{ProductSimplex{Tuple{SymbolicSimplex{Symbol}, SymbolicSimplex{Symbol}}}, Int64} with 0 terms:
0
```
