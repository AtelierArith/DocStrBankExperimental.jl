```
BiPowerXdata(DM::AbstractDataModel) -> AbstractDataModel
BiPowerXdata(DS::AbstractDataSet) -> AbstractDataSet
```

Returns a modified `DataModel` or dataset object where BiPower has been applied component-wise to the x-variables both in the data as well as for the model. The uncertainties are computed via linearized error propagation through the given transformation.
