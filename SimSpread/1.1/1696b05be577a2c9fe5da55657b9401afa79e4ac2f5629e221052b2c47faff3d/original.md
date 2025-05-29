```
featurize!(X::NamedArray, α::AbstractFloat, weighted::Bool=true)
```

Transform, in place, the feature matrix `X` into a SimSpread feature matrix.

# Arguments

  * `X::NamedArray` : Continuous feature matrix
  * `α::AbstractFloat` : Featurization cutoff
  * `weighted::Bool` : Apply weighting function to outcome (default = true)

# References

1. Vigil-Vásquez & Schüller (2022). De Novo Prediction of Drug Targets and Candidates by Chemical Similarity-Guided Network-Based Inference. International Journal of Molecular Sciences, 23(17), 9666. https://doi.org/10.3390/ijms23179666
