```
predictedarray(r, data::RNAOnOffData, model::AbstractGeneTransitionModel)
```

Calculates the likelihood for RNA On/Off data.

# Arguments

  * `r`: The rates.
  * `data::RNAOnOffData`: The RNA On/Off data.
  * `model::AbstractGeneTransitionModel`: The model.

# Returns

  * `Array{Float64,1}`: The likelihoods for the RNA On/Off data.
