```
catch22(𝐱::Vector)
catch22(X::Array)
catch22[featurename::Symbol](X::Array)
```

Evaluate all features for a time series vector `𝐱` or the columns of an array `X`. `catch22` is a FeatureSet, which means it can be indexed by feature names (as symbols) to return a subset of the available features. `getnames(catch22)`, `getkeywords(catch22)` and `getdescriptions(catch22)` will also return feature names, keywords and descriptions respectively. Features are returned in a `FeatureArray`, in which array rows are annotated by feature names. A `FeatureArray` can be converted to a regular array with `Array(F)`.

# Examples

```julia
𝐱 = Catch22.testdata[:test]
𝐟 = catch22(𝐱)

X = randn(100, 10)
F = catch22(X)
F = catch22[:DN_HistogramMode_5](X)
```
