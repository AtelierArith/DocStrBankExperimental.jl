```
DetermineDmodel(DS::AbstractDataSet, model::Function; ADmode::Union{Symbol,Val}=:ForwardDiff)::Function
```

Returns appropriate function which constitutes the automatic derivative of the `model(x,θ)` with respect to the parameters `θ` depending on the format of the x-values and y-values of the DataSet.
