```
bitrand([rng=default_rng()], [dims...])
```

Generate a `BitArray` of random boolean values.

# Examples

```jldoctest
julia> rng = MersenneTwister(1234);

julia> bitrand(rng, 10)
10-element BitVector:
 0
 0
 0
 0
 1
 0
 0
 0
 1
 1
```
