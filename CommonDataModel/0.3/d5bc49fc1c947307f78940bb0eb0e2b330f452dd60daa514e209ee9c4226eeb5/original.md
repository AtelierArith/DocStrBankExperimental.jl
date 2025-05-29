```
v = CommonDataModel.defVar(ds::AbstractDataset,src::AbstractVariable)
v = CommonDataModel.defVar(ds::AbstractDataset,name::SymbolOrString,src::AbstractVariable)
```

Defines and return the variable in the data set `ds` copied from the variable `src`. The dimension name, attributes and data are copied from `src` as well as the variable name (unless provide by `name`).
