```
shih_opp(z::ProductSimplex{T}) where T <: Tuple{AbstractSimplex,AbstractSimplex} -> Linear{T}
```

Return the image of the product simplex `z` under the *opposite* Eilenberg–MacLane homotopy (which is sometimes called the opposite Shih map).

This function is linear and supports the keyword arguments `coefftype`, `addto`, `coeff`, `sizehint` and `is_filtered` as described for the macro `@linear`.

See also [`aw`](@ref), [`ez`](@ref), [`shih`](@ref), [`opposite`](@ref), [`swap`](@ref), `LinearCombinations.@linear`.

# Example

```jldoctest
julia> x, y = SymbolicSimplex(:x, 2), SymbolicSimplex(:y, 2)
(x[0,1,2], y[0,1,2])

julia> a = Linear(ProductSimplex(x, y) => 1)   # we use `Linear` to get the correct sign from `opposite` below
Linear{ProductSimplex{Tuple{SymbolicSimplex{Symbol}, SymbolicSimplex{Symbol}}}, Int64} with 1 term:
(x[0,1,2],y[0,1,2])

julia> shih_opp(a)
Linear{ProductSimplex{Tuple{SymbolicSimplex{Symbol}, SymbolicSimplex{Symbol}}}, Int64} with 4 terms:
-(x[0,0,0,2],y[0,1,2,2])+(x[0,0,1,2],y[0,1,1,2])+(x[0,0,1,2],y[1,2,2,2])-(x[0,1,1,2],y[1,1,2,2])

julia> shih(a)
Linear{ProductSimplex{Tuple{SymbolicSimplex{Symbol}, SymbolicSimplex{Symbol}}}, Int64} with 4 terms:
-(x[0,1,1,2],y[0,1,2,2])+(x[0,0,1,1],y[0,1,1,2])-(x[0,0,0,1],y[0,1,2,2])+(x[0,0,1,2],y[0,2,2,2])

julia> shih_opp(opposite(swap(a))) == opposite(swap(shih(a)))
true
```
