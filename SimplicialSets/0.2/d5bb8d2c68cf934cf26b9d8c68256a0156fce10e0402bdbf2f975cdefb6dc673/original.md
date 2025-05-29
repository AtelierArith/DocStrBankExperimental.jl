```
ProductSimplex{T<:Tuple{Vararg{AbstractSimplex}}} <: AbstractSimplex

ProductSimplex{T}{t::Tuple{Vararg{AbstractSimplex}} [; dim::Integer]}

ProductSimplex(t::Tuple{Vararg{AbstractSimplex}} [; dim::Integer])
ProductSimplex(xs::AbstractSimplex... [; dim::Integer])
```

A type representing an element in the product of simplicial sets. Empty products are allowed. The component simplices must all be of the same dimension. They may be given as a tuple or as individual arguments.

In the case of the empty product, the keyword argument `dim` is required to determine the dimension of the resulting simplex. Otherwise `dim` is optional, but if present, it must be correct.

See also [`Tuple(x::ProductSimplex)`](@ref).

# Examples

```jldoctest
julia> x, y = SymbolicSimplex(:x, 2), SymbolicSimplex(:y, 2)
(x[0,1,2], y[0,1,2])

julia> z = ProductSimplex(x, y)
(x[0,1,2],y[0,1,2])

julia> w = ProductSimplex(dim = 2)
()

julia> dim(w)
2

julia> ProductSimplex(x, y; dim = 1)
ERROR: dimensions of simplices do not match
[...]
```
