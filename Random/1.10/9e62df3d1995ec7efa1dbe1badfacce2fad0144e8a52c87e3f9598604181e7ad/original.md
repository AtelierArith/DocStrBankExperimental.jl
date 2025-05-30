```
rand!([rng=default_rng()], A, [S=eltype(A)])
```

Populate the array `A` with random values. If `S` is specified (`S` can be a type or a collection, cf. [`rand`](@ref) for details), the values are picked randomly from `S`. This is equivalent to `copyto!(A, rand(rng, S, size(A)))` but without allocating a new array.

# Examples

```jldoctest
julia> rng = MersenneTwister(1234);

julia> rand!(rng, zeros(5))
5-element Vector{Float64}:
 0.5908446386657102
 0.7667970365022592
 0.5662374165061859
 0.4600853424625171
 0.7940257103317943
```
