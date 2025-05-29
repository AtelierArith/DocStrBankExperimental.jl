```
function ridge(f::StatsModels.FormulaTerm, df::DataFrames.AbstractDataFrame, ks::AbstractRange ; 
weights::Union{Nothing,String}=nothing, remove_missing=false, contrasts=nothing, traceplots=false)

Ridge regression, expects a range of k parameter (also known as k).
When weights are provided, result in a weighted ridge regression.
When traceplots are requested, also return a dictionnary of trace plots.
```
