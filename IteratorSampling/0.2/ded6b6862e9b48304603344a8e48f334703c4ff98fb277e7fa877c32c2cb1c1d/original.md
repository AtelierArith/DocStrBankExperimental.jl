```
reservoir_sample(rng, iter, [wv]; method = :alg_L)
reservoir_sample(rng, iter, [wv], n; replace = false, ordered = false, kwargs...)
```

Reservoir sampling algorithm with and without replacement.

The optional `kwargs` are passed to more specific methods called internally by the  function, which can either be 

  * [`reservoir_sample_without_replacement`](@ref)
  * [`reservoir_sample_with_replacement`](@ref)
  * [`weighted_reservoir_sample_without_replacement`](@ref)
  * [`weighted_reservoir_sample_with_replacement`](@ref)

depending to the kind of sampling performed.
