```
randcycle!([rng=default_rng(),] A::Array{<:Integer})
```

Construct in `A` a random cyclic permutation of length `length(A)`. The optional `rng` argument specifies a random number generator, see [Random Numbers](@ref).

# Examples

```jldoctest
julia> randcycle!(MersenneTwister(1234), Vector{Int}(undef, 6))
6-element Vector{Int64}:
 3
 5
 4
 6
 1
 2
```
