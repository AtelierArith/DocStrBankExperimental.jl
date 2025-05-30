```
randsubseq!([rng=default_rng(),] S, A, p)
```

Like [`randsubseq`](@ref), but the results are stored in `S` (which is resized as needed).

# Examples

```jldoctest
julia> rng = MersenneTwister(1234);

julia> S = Int64[];

julia> randsubseq!(rng, S, 1:8, 0.3)
2-element Vector{Int64}:
 7
 8

julia> S
2-element Vector{Int64}:
 7
 8
```
