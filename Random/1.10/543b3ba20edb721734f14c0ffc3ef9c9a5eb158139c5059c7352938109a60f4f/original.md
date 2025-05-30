```
MersenneTwister(seed)
MersenneTwister()
```

Create a `MersenneTwister` RNG object. Different RNG objects can have their own seeds, which may be useful for generating different streams of random numbers. The `seed` may be a non-negative integer or a vector of `UInt32` integers. If no seed is provided, a randomly generated one is created (using entropy from the system). See the [`seed!`](@ref) function for reseeding an already existing `MersenneTwister` object.

# Examples

```jldoctest
julia> rng = MersenneTwister(1234);

julia> x1 = rand(rng, 2)
2-element Vector{Float64}:
 0.5908446386657102
 0.7667970365022592

julia> rng = MersenneTwister(1234);

julia> x2 = rand(rng, 2)
2-element Vector{Float64}:
 0.5908446386657102
 0.7667970365022592

julia> x1 == x2
true
```
