```
CategoricalNetwork(model)([rng,] state::AbstractArray [, mask::AbstractArray{Bool}]; is_sampling::Bool=false, is_return_log_prob::Bool = false)
```

CategoricalNetwork wraps a model (typically a neural network) that takes a `state` input  and outputs logits for a categorical distribution. The optional argument `mask` must be an Array of `Bool` with the same size as `state` expect for the first dimension that must have the length of the action vector. Actions mapped to `false` by mask have a logit equal to  `-Inf` and/or a zero-probability of being sampled.

  * `rng::AbstractRNG=Random.default_rng()`
  * `is_sampling::Bool=false`, whether to sample from the obtained normal categorical distribution (returns a Flux.OneHotArray `z`).
  * `is_return_log_prob::Bool=false`, whether to return the *logits* (i.e. the unnormalized logprobabilities) of getting the sampled actions in the given state.

Only applies if `is_sampling` is true and will return `z, logits`.

If `is_sampling = false`, returns only the logits obtained by a simple forward pass into `model`.
