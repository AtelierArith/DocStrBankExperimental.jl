```
rand([rng::AbstractRNG,]
      model::TraitSubstitutionModel,
      t::Float64,
      start::AbstractVector{Int})
```

Simulate discrete traits along one edge of length t. A random number generator `rng` is optional. `start` must be a vector of integers, each representing the starting value of one trait.

# examples

```jldoctest
julia> m1 = BinaryTraitSubstitutionModel(1.0, 2.0)
Binary Trait Substitution Model:
rate 0→1 α=1.0
rate 1→0 β=2.0

julia> using StableRNGs; rng = StableRNG(135);

julia> rand(rng, m1, 0.2, [1,2,1,2,1])
5-element Vector{Int64}:
 2
 2
 1
 2
 1
```
