```
update_param!(mi::ModelInstance, comp_name::Symbol, param_name::Symbol, value)
```

Update the `value` of a model parameter in `ModelInstance` `mi`, connected to  component `comp_name`'s parameter `param_name`. This is an UNSAFE updat as it does  not dirty the model, and should  be used carefully and specifically for things like  our MCS work.
