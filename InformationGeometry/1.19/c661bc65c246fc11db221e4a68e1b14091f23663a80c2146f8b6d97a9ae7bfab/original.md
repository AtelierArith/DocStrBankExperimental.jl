```
Exp10Ydata(DM::AbstractDataModel) -> AbstractDataModel
Exp10Ydata(DS::AbstractDataSet) -> AbstractDataSet
```

Returns a modified `DataModel` or dataset object where exp10 has been applied component-wise to the y-variables both in the data as well as for the model. The uncertainties are computed via linearized error propagation through the given transformation.
