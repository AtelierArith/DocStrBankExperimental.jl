```
WoodburyEstimator(loss::LossFunction, rank::Integer;
                  σ²::Union{Real,Nothing}=nothing, corrected::Bool=false)
```

Specify that covariance matrices should be estimated using a "spiked" covariance model

```
Σ = σ²I + U * Λ * U'
```

`loss` is either a [`NormLossCov`](@ref) or [`StatLossCov`](@ref) object, which specifies the loss function for which the estimated covariance will be optimal. `rank` is the maximum number of eigenvalues `Λ` to retain in the model. Optionally, one may specify `σ²` directly, or it can be estimated from the data matrix (`σ²=nothing`). Set `corrected=true` to use the unbiased estimator of the variance.
