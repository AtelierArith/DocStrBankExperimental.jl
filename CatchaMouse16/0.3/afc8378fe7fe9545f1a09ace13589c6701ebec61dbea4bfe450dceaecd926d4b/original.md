```
catchaMouse16(𝐱::Vector)
catchaMouse16(X::Array)
catchaMouse16[featurename::Symbol](X::Array)
```

Evaluate all features for a time series vector `𝐱` or the columns of an array `X`. `catchaMouse16` is a FeatureSet, which means it can be indexed by feature names (as symbols) to return a subset of the available features. `getnames(catchaMouse16)`, `getkeywords(catchaMouse16)` and `getdescriptions(catchaMouse16)` will also return feature names, keywords and descriptions respectively. Features are returned in a `FeatureArray`, in which array rows are annotated by feature names. A `FeatureArray` can be converted to a regular array with `Array(F)`.

# Examples

```julia
𝐱 = CatchaMouse16.testdata[:test]
𝐟 = catchaMouse16(𝐱)

X = randn(100, 10)
F = catchaMouse16(X)
F = catchaMouse16[:AC_nl_035](X)
```
