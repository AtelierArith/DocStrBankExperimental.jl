```
detectAnomalies(data::AbstractArray{tp, N}, P::PARAMS) where {tp, N}
detectAnomalies(data::AbstractArray{tp, N}, algorithms::Array{String,1} = ["REC", "KDE"]; mean = 0) where {tp, N}
```

detect anomalies, given some Parameter object `P` of type PARAMS. Train the Parameters `P` with `getParameters()` beforehand on some training data. See `getParameters()`. Without training `P` beforehand, it is also possible to use `detectAnomalies(data, algorithms)` given some algorithms (except SVDD, KNFST). Some default parameters are used in this case to initialize `P` internally.

# Examples

```
julia> training_data = randn(100, 2); testing_data = randn(100, 2);
julia> # compute the anoamly scores of the algorithms "REC", "KDE", "T2" and "KNN_Gamma", their quantiles and return their ensemble scores
julia> P = getParameters(["REC", "KDE", "T2", "KNN_Gamma"], training_data, quantiles = true, ensemble_method = "mean");
julia> detectAnomalies(testing_data, P)
```
