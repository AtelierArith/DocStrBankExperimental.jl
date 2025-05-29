```
add_shared_param!(md::ModelDef, name::Symbol, value::Any; dims::Array{Symbol}=Symbol[])
```

User-facing API function to add a shared parameter to Model Def `md` with name `name` and value `value`, and an array of dimension names `dims` which dfaults to  an empty vector.  The `is_shared` attribute of the added Model Parameter will be `true`.

The `value` can by a scalar, an array, or a NamedAray. Optional keyword argument 'dims' is a list of the dimension names of the provided data, and will be used to check that they match the model's index labels. Optional keyword argument `datatype` allows user to specify a datatype to use for the shared model parameter.
