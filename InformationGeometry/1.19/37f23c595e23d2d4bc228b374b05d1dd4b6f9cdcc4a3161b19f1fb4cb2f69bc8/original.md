```
Exp10Xdata(DM::AbstractDataModel, idxs::BoolVector) -> AbstractDataModel
Exp10Xdata(DS::AbstractDataSet, idxs::BoolVector) -> AbstractDataSet
```

Returns a modified `DataModel` or dataset object where exp10 has been applied to the components `i` of the x-variables for which `idxs[i]==true` both in the data as well as for the model. The uncertainties are computed via linearized error propagation through the given transformation.
