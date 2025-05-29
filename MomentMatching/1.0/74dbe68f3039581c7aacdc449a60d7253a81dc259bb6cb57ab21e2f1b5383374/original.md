```julia
indexvector(
    mode::MomentMatching.EstimationMode,
    modelname::String
)

```

Create a logical vector selecting the parameters which are actually estimated from the possible full list (see full*labels in [`parambounds`](@ref)). If the `i`th element of the resulting vector is `true`, then the `i`th parameter from `full*labels` will be estimated. 

When for an EstimationMode a matching method is not separately defined, it assumes all possible parameters are always estimated and thus defaults to a vector of `true` values.
