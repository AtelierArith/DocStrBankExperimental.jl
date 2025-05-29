```
(model::SoftGaussianNetwork)(rng::AbstractRNG, state::AbstractArray{<:Any, 3}, action_samples::Int)
```

Sample `action_samples` actions from each state. Returns a 3D tensor with dimensions `(action_size x action_samples x batchsize)`. `state` must be 3D tensor with dimensions `(state_size x 1 x batchsize)`. Always returns the logpdf of each action along.
