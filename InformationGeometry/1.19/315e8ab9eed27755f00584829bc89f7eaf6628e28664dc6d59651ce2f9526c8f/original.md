```
BiPowerYdata(DM::AbstractDataModel, idxs::BoolVector) -> AbstractDataModel
BiPowerYdata(DS::AbstractDataSet, idxs::BoolVector) -> AbstractDataSet
```

Returns a modified `DataModel` or dataset object where BiPower has been applied to the components `i` of the y-variables for which `idxs[i]==true` both in the data as well as for the model. The uncertainties are computed via linearized error propagation through the given transformation.
