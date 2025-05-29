```
set_param!(md::ModelDef, comp_name::Symbol,
           value_dict::Dict{Symbol, Any}, param_names)
```

Call `set_param!()` for each name in `param_names`, retrieving the corresponding value from `value_dict[param_name]`.
