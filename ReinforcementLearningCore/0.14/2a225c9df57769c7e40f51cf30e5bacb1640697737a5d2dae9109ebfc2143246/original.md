```
(model::CovGaussianNetwork)(rng::AbstractRNG, state::AbstractMatrix; is_sampling::Bool=false, is_return_log_prob::Bool=false)
```

Given a Matrix of states, will return actions, μ and logpdf in matrix format. The batch of Σ remains a 3D tensor.
