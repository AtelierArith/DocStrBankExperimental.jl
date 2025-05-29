```
FixedAtomsProbabilityDistribution{threaded}
```

A probability distribution with finite support and fixed atoms.

Whenever its expectation is differentiated, only the weights are considered active, whereas the atoms are considered constant.

# Example

```jldoctest
julia> using DifferentiableExpectations, Statistics, Zygote

julia> using DifferentiableExpectations: atoms, weights

julia> dist = FixedAtomsProbabilityDistribution([2, 3], [0.4, 0.6]);

julia> atoms(map(abs2, dist))
2-element Vector{Int64}:
 4
 9

julia> weights(map(abs2, dist))
2-element Vector{Float64}:
 0.4
 0.6

julia> mean(abs2, dist)
7.0

julia> gradient(mean, abs2, dist)[2]
(atoms = nothing, weights = [4.0, 9.0])
```

# Constructor

```
FixedAtomsProbabilityDistribution(
    atoms::AbstractVector,
    weights::AbstractVector=uniform_weights(atoms);
    threaded=false
)
```

# Fields

  * `atoms::AbstractVector`
  * `weights::AbstractVector{<:Real}`
