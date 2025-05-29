```julia
fullfactorial(
    factors::Tuple
) -> Base.Iterators.ProductIterator

```

Receives a tuple of arrays representing categorical factor levels, and returns a `Base.Iterators.ProductIterator`.   This allows  full  factorial  designs to  be arbitrarily large and  only be computed as needed.  To  compute an explicit full factorial design, use [`explicit_fullfactorial`](@ref).

```jldoctest
julia> fullfactorial(Tuple([-1, 1] for i = 1:10))
Base.Iterators.ProductIterator{NTuple{10, Vector{Int64}}}(([-1, 1], [-1, 1], [-1, 1], [-1, 1], [-1, 1], [-1, 1], [-1, 1], [-1, 1], [-1, 1], [-1, 1]))

```
