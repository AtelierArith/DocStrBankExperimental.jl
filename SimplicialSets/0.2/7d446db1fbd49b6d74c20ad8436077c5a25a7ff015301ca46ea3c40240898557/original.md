```
Lattice{N} <: AbstractVector{Int}

Lattice(t::NTuple{N,Integer}) where N -> Lattice{N}
Lattice(x::Integer...) -> Lattice
```

A type representing elements in a lattice (free abelian group) of rank `N`.

See also [`Tuple(::Lattice)`](@ref).

# Examples

```jldoctest
julia> x, y = Lattice(1, 2, 3), Lattice(0, -1, 5)
((1, 2, 3), (0, -1, 5))

julia> x+y, x-y
((1, 1, 8), (1, 3, -2))

julia> 2*x
3-element Lattice{3}:
 2
 4
 6

julia> zero(x)
3-element Lattice{3}:
 0
 0
 0

julia> length(x)
3

julia> y[2]
-1

julia> a, z... = x; z
2-element Vector{Int64}:
 2
 3
```
