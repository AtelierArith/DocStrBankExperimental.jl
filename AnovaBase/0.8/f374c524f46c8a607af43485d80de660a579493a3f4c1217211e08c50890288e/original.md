```
anovatable(aov::AnovaResult{<: FullModel, Test}; rownames = prednames(aov))
anovatable(aov::AnovaResult{<: MultiAovModels, Test}; rownames = string.(1:N))
anovatable(aov::AnovaResult{<: MultiAovModels, FTest, N}; rownames = string.(1:N)) where N
anovatable(aov::AnovaResult{<: MultiAovModels, LRT, N}; rownames = string.(1:N)) where N
```

Return a table with coefficients and related statistics of ANOVA.

When displaying `aov` in repl, `rownames` will be `prednames(aov)` for [`FullModel`](@ref) and `string.(1:N)` for [`MultiAovModels`](@ref). 

For `MultiAovModels`, there are two default methods for `FTest` and `LRT`; one can also define new methods dispatching on `::AnovaResult{NestedModels{M}}` or `::AnovaResult{MixedAovModels{M}}` where `M` is a model type. 

For `FullModel`, no default api is implemented.

The returned `AnovaTable` object implements the [`Tables.jl`](https://github.com/JuliaData/Tables.jl/) interface, and can be   converted e.g. to a DataFrame via `using DataFrames; DataFrame(anovatable(aov))`.
