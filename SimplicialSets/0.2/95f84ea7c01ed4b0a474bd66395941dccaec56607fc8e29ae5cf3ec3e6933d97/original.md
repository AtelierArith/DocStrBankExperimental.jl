```
BarSimplex{T} <: AbstractSimplex

BarSimplex(iter; op::Union{typeof(*),typeof(+)} = *) -> BarSimplex
```

A type representing simplices in a simplicial bar construction. If `T` is a subtype of `AbstractSimplex`, then it is assumed to be a simplicial group; otherwise `T` is assumed to be a multiplicative discrete group.

The constructor accepts an iterator over the components of the bar simplex. The optional keyword `op` indicates whether the group is multiplicative (default) or additive.

Iterating over a `BarSimplex` means iterating over its components.

See also [`AddToMul`](@ref).

# Examples

```jldoctest
julia> using SimplicialSets: d, s

julia> b = BarSimplex([Lattice(1, 2), Lattice(3, 4)]; op = +)
[(1, 2),(3, 4)]

julia> d(b, 0)
[(3, 4)]

julia> d(b, 1)
[(4, 6)]

julia> s(b, 1)
[(1, 2),(0, 0),(3, 4)]

julia> collect(b)
2-element Vector{AddToMul{Lattice{2}}}:
 (1, 2)
 (3, 4)

julia> b1 = BarSimplex([Lattice(1, 2)]; op = +)
[(1, 2)]

julia> b0 = BarSimplex(Lattice{2}[]; op = +)
[]

julia> c = BarSimplex([b0, b1])
[[],[(1, 2)]]

julia> s(c, 1)
[[],[(0, 0)],[(0, 0),(1, 2)]]
```
