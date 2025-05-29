```
getParameters(algorithms::Array{String,1} = ["REC", "KDE"], training_data::AbstractArray{tp, 2} = [NaN NaN])
```

return an object of type PARAMS, given the `algorithms` and some `training_data` as a matrix.

# Arguments

  * `algorithms`: Subset of `["REC", "KDE", "KNN_Gamma", "KNN_Delta", "SVDD", "KNFST", "T2"]`
  * `training_data`: data for training the algorithms / for getting the Parameters.
  * `dist::String = "Euclidean"`
  * `sigma_quantile::Float64 = 0.5` (median): quantile of the distance matrix, used to compute the weighting parameter for the kernel matrix (`algorithms = ["SVDD", "KNFST", "KDE"]`)
  * `varepsilon_quantile` = `sigma_quantile` by default: quantile of the distance matrix to compute the radius of the hyperball in which the number of reccurences is counted (`algorihtms = ["REC"]`)
  * `k_perc::Float64 = 0.05`: percentage of the first dimension of `training_data` to estimmate the number of nearest neighbors (`algorithms = ["KNN-Gamma", "KNN_Delta"]`)
  * `nu::Float64 = 0.2`: use the maximal percentage of outliers for `algorithms = ["SVDD"]`
  * `temp_excl::Int64 = 0`. Exclude temporal adjacent points from beeing count as recurrences of k-nearest neighbors `algorithms = ["REC", "KNN-Gamma", "KNN_Delta"]`
  * `ensemble_method = "None"`: compute an ensemble of the used algorithms. Possible choices (given in `compute_ensemble()`) are "mean", "median", "max" and "min".
  * `quantiles = false`: convert the output scores of the algorithms into quantiles.

# Examples

```
julia> using MultivariateAnomalies
julia> training_data = randn(100, 2); testing_data = randn(100, 2);
julia> P = getParameters(["REC", "KDE", "SVDD"], training_data, quantiles = false);
julia> detectAnomalies(testing_data, P)
```
