```
TransformXdata(DM::AbstractDataModel, Emb::Function, iEmb::Function, TransformName::String="Trafo") -> AbstractDataModel
TransformXdata(DS::AbstractDataSet, Emb::Function, TransformName::String="Trafo") -> AbstractDataSet
```

Returns a modified `DataModel` where the x-variables have been transformed by a multivariable transform `Emb` both in the data as well as for the model via `newmodel(x,θ) = oldmodel(Emb(x),θ)`. `iEmb` denotes the inverse of `Emb`. The uncertainties are computed via linearized error propagation through the given transformation.
