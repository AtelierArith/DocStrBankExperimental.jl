```
BiLogXdata(DM::AbstractDataModel, idxs::BoolVector) -> AbstractDataModel
BiLogXdata(DS::AbstractDataSet, idxs::BoolVector) -> AbstractDataSet
```

Returns a modified `DataModel` or dataset object where BiLog has been applied to the components `i` of the x-variables for which `idxs[i]==true` both in the data as well as for the model. The uncertainties are computed via linearized error propagation through the given transformation.
