```
delete_param!(m::Model, model_param_name::Symbol)
```

Delete `model_param_name` from a model `m`'s ModelDef's list of model parameters, and also remove all external parameters connections that were connected to `model_param_name`.
