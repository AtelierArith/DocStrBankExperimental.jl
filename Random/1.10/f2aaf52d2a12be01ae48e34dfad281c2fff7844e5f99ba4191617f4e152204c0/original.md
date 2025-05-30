```
randexp!([rng=default_rng()], A::AbstractArray) -> A
```

Fill the array `A` with random numbers following the exponential distribution (with scale 1).

# Examples

```jldoctest
julia> rng = MersenneTwister(1234);

julia> randexp!(rng, zeros(5))
5-element Vector{Float64}:
 2.4835053723904896
 1.516703605376473
 0.6044364871025417
 0.6958665886385867
 1.3065196315496677
```
