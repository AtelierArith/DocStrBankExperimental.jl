```
ez(x::AbstractSimplex...) -> ProductSimplex

ez(AbstractTensor{T}) where T <: Tuple{Vararg{AbstractSimplex}} -> ProductSimplex{T}
```

Return the image of the given simplices under the Eilenberg–Zilber or shuffle map. The first version is multilinear in the simplices and the second one linear in the tensor argument. Any number of simplices is allowed, including zero.

This function supports the keyword arguments `coefftype`, `addto`, `coeff`, `sizehint` and `is_filtered` as described for the macro `@linear`.

See also [`aw`](@ref), [`shih`](@ref), `LinearCombinations.@linear`.

# Examples

```jldoctest
julia> x, y = SymbolicSimplex(:x, 1), SymbolicSimplex(:y, 2)
(x[0,1], y[0,1,2])

julia> a = ez(x, y)
Linear{ProductSimplex{Tuple{SymbolicSimplex{Symbol}, SymbolicSimplex{Symbol}}}, Int64} with 3 terms:
(x[0,1,1,1],y[0,0,1,2])-(x[0,0,1,1],y[0,1,1,2])+(x[0,0,0,1],y[0,1,2,2])

julia> ez(Tensor(x, y); addto = a, coeff = -1)
Linear{ProductSimplex{Tuple{SymbolicSimplex{Symbol}, SymbolicSimplex{Symbol}}}, Int64} with 0 terms:
0

julia> z = SymbolicSimplex(:z, 0)
z[0]

julia> ez(x, y, z)
Linear{ProductSimplex{Tuple{SymbolicSimplex{Symbol}, SymbolicSimplex{Symbol}, SymbolicSimplex{Symbol}}}, Int64} with 3 terms:
(x[0,1,1,1],y[0,0,1,2],z[0,0,0,0])-(x[0,0,1,1],y[0,1,1,2],z[0,0,0,0])+(x[0,0,0,1],y[0,1,2,2],z[0,0,0,0])

julia> ez(x, y, z) == ez(ez(x, y), z)
false

julia> ez(x)
Linear{ProductSimplex{Tuple{SymbolicSimplex{Symbol}}}, Int64} with 1 term:
(x[0,1])

julia> ez(Tensor())
Linear{ProductSimplex{Tuple{}}, Int64} with 1 term:
()
```
