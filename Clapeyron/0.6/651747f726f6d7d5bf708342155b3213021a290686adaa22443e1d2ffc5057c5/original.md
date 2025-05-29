```
export_model(model::EoSModel,name="";location=".")
```

Exports model parameters to CSVs. Unless the `name` kwarg is specified, the name of the files will follow the convention `singledata_EoS`, `pairdata_EoS` and `assocdata_EoS`. Files will be saved within the current directory unless the `location` argument is specified.

Note that it will export all submodel parameters (e.g. Alpha function parameters for cubic EoS).
