```
summarizeEstimates(samples)
summarizeEstimates(samples; savetofile="ite_samples.csv")
```

Summarize Predicted Estimates (Counterfactual Outcomes or Individual Treatment Effects)

Create dataframe of mean, lower and upper quantiles of the samples from [`sampleITE`](@ref) or [`predictCounterfactualEffects`](@ref).

Params:

  * `samples`: The `n x m` array of samples from sampleSATE or sampleITE
  * `savetofile::String`: Optionally save the resultant DataFrame as CSV to the filename passed
  * `credible_interval::Float64`: A real in [0,1] where 0.90 is the default for a 90% credible interval

Returns:

  * `df`: Dataframe of Individual, Mean, LowerBound, and UpperBound values for the credible intervals around the sample.
