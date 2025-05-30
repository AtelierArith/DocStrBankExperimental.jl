```
randcycle([rng=default_rng(),] n::Integer)
```

Construct a random cyclic permutation of length `n`. The optional `rng` argument specifies a random number generator, see [Random Numbers](@ref). The element type of the result is the same as the type of `n`.

!!! compat "Julia 1.1"
    In Julia 1.1 `randcycle` returns a vector `v` with `eltype(v) == typeof(n)` while in Julia 1.0 `eltype(v) == Int`.


# Examples

```jldoctest
julia> randcycle(MersenneTwister(1234), 6)
6-element Vector{Int64}:
 3
 5
 4
 6
 1
 2
```
