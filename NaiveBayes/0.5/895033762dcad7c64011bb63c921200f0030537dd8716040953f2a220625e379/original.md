Initialize a `HybridNB` model with continuous and/or discrete features

### Constructors

```julia
HybridNB(labels::AbstractVector, kde_names::AbstractVector, discrete_names::AbstractVector)
HybridNB(labels::AbstractVector, kde_names::AbstractVector)
HybridNB(labels::AbstractVector, num_kde::Int, num_discrete::Int)
```

### Arguments

  * `labels` : An AbstractVector{Any} of feature labels
  * `kde_names` : An AbstractVector{Any} of the names of continuous features
  * `discrete_names` : An AbstractVector{Any} of the names of discrete features
  * `num_kde` : Number of continuous features
  * `num_discrete` : Number of discrete features
