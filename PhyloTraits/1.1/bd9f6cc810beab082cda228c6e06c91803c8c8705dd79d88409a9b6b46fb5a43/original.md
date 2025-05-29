```
rand!(rng::AbstractRNG,
      end::AbstractVector{Int},
      model::TraitSubstitutionModel,
      t::Float64,
      start::AbstractVector{Int})
```

Simulate discrete traits along one edge of length `t` like [`rand`](@ref PhyloTraits.rand), but modifying `end` in place to store the simulated values.
