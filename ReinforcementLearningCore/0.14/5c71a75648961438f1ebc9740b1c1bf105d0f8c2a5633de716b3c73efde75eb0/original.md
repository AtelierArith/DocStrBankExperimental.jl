```
(model::CovGaussianNetwork)(state::AbstractArray, action::AbstractArray)
```

Return the logpdf of the model sampling `action` when in `state`.  State must be a 3D tensor with dimensions `(state_size x 1 x batchsize)`.  Multiple actions may be taken per state, `action` must have dimensions `(action_size x action_samples_per_state x batchsize)`. Returns a 3D tensor with dimensions `(1 x action_samples_per_state x batchsize)`.
