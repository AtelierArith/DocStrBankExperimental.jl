```
predictedfn(param, data::AbstractHistogramData, model::AbstractGeneTransitionModel)
```

Calculates the likelihood for multiple histograms.

# Arguments

  * `param`: The model parameters.
  * `data::AbstractHistogramData`: The histogram data.
  * `model::AbstractGeneTransitionModel`: The model.

# Returns

  * `Array{Float64,2}`: An array of likelihoods for the histograms.
