```
(model::CategoricalNetwork)([rng::AbstractRNG,] state::AbstractArray{<:Any, 3}, [mask::AbstractArray{Bool},] action_samples::Int)
```

Sample `action_samples` actions from each state. Returns a 3D tensor with dimensions `(action_size x action_samples x batchsize)`.  Always returns the *logits* of each action along in a tensor with the same dimensions. The optional argument `mask` must be an Array of `Bool` with the same size as `state` expect for the first dimension that must have the length of the action vector. Actions mapped to `false` by mask have a logit equal to  `-Inf` and/or a zero-probability of being sampled.
