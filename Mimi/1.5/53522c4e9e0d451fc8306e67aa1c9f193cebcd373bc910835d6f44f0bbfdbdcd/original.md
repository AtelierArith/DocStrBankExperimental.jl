```
update_param!(mi::ModelInstance, name::Symbol, value)
```

Update the `value` of a model parameter in `ModelInstance` `mi`, referenced by `name`.  This is an UNSAFE update as it does not dirty the model, and should  be used carefully and specifically for things like our MCS work.
