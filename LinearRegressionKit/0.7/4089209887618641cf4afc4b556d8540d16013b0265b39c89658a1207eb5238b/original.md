```
function ridge(f::StatsModels.FormulaTerm, df::DataFrames.AbstractDataFrame, k::Float64 ; 
weights::Union{Nothing,String}=nothing, remove_missing=false, contrasts=nothing)

Ridge regression, expects a k parameter (also known as k).
When weights are provided, result in a weighted ridge regression.
```
