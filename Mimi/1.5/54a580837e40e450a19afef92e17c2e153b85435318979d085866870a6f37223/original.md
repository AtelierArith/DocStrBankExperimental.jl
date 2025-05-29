```
delete_param!(md::ModelDef, model_param_name::Symbol)
```

Delete `model_param_name` from `md`'s list of model parameters, and also  remove all external parameters connections that were connected to `model_param_name`.
