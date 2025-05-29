```
export_model(model, name, file::IO)
export_model(model, name, path::String)
```

Export the model into a module file. The `name` parameter is used for the name of the module as well as the module file. The module file is created in the directory specified by the optional third argument.
