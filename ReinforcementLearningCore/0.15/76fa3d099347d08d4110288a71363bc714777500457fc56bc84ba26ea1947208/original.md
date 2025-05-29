```
(model::CovGaussianNetwork)(rng::AbstractRNG, state::AbstractArray{<:Any, 3}, action_samples::Int)
```

Sample `action_samples` actions per state in `state` and return the `actions, logpdf(actions)`.  This function is compatible with a multidimensional action space.  The outputs are 3D tensors with dimensions `(action_size x action_samples x batchsize)` and `(1 x action_samples x batchsize)` for `actions` and `logdpf` respectively.
