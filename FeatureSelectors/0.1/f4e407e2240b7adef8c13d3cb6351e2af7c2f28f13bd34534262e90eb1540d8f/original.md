```
select_features(selector,
                X::DataFrame,
                y::Vector;
                verbose::Bool=false)
```

Select features based on the importance, which is defined by `selector.method` to target `y`. if `verbose` is true, logs will be printed - this defaults to false. This function will return only the feature names of selected features.

If you have feature `X_data` as matrix and feature names `X_features` as a Vector, you can replace `X` with `X_data` and `X_features` (in this order).

# Example

```jldoctest
julia> using RDatasets, FeatureSelectors, DataFrames

julia> boston = dataset("MASS", "Boston");

julia> selector = UnivariateFeatureSelector(method=pearson_correlation, k=5)
UnivariateFeatureSelector(FeatureSelectors.pearson_correlation, 5, nothing)

julia> select_features(
           selector,
           boston[:, Not(:MedV)],
           boston.MedV
       )
5-element Vector{String}:
 "LStat"
 "Rm"
 "PTRatio"
 "Indus"
 "Tax"

```
