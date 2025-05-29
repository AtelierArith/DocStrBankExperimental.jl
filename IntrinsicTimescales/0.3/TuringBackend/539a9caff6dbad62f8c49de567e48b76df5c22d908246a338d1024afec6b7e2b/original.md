```
ADVIResults{T<:Real}
```

Container for ADVI (Automatic Differentiation Variational Inference) results.

# Fields

  * `samples::AbstractArray{T}`: Matrix of posterior samples
  * `MAP::AbstractVector{T}`: Maximum a posteriori estimates
  * `variances::AbstractVector{T}`: Posterior variances for each parameter
  * `chain`: Turing chain object containing full inference results
