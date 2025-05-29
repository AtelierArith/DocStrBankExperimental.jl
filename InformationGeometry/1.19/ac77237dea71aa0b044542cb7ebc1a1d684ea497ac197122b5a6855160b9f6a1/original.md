```
ComponentwiseModelTransform(DM::AbstractDataModel, F::Function, idxs=trues(pdim(DM))) -> DataModel
ComponentwiseModelTransform(model::Function, idxs, F::Function) -> Function
```

Transforms the parameters of the model by the given scalar function `F` such that `newmodel(x, θ) = oldmodel(x, F.(θ))`. By providing `idxs`, one may restrict the application of the function `F` to broadcast only to specific parameter components.

For vector-valued transformations, see [`ModelEmbedding`](@ref).
