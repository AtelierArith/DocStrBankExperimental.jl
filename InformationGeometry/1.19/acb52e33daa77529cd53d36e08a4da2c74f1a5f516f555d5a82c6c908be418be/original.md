```
ModelEmbedding(DM::AbstractDataModel, F::Function, start::AbstractVector; Domain::HyperCube=FullDomain(length(start),Inf)) -> DataModel
```

Transforms a model function via `newmodel(x, θ) = oldmodel(x, F(θ))` and returns the associated `DataModel`. An initial parameter configuration `start` as well as a `Domain` can optionally be passed to the `DataModel` constructor.

For component-wise transformations see [`ComponentwiseModelTransform`](@ref).
