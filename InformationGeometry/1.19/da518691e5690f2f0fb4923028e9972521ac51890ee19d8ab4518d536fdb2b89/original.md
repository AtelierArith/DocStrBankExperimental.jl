```
TransformYdata(DM::AbstractDataModel, Emb::Function, TransformName::String="Trafo") -> AbstractDataModel
TransformYdata(DS::AbstractDataSet, Emb::Function, TransformName::String="Trafo") -> AbstractDataSet
```

Returns a modified `DataModel` where the y-variables have been transformed by a multivariable transform `Emb` both in the data as well as for the model via `newmodel(x,θ) = Emb(oldmodel(x,θ))`. The uncertainties are computed via linearized error propagation through the given transformation.
