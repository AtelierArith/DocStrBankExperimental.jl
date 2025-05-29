```
register_global!(types::ModelTypes, name::Symbol, default_value::T)
```

There are two ways to set up globals for a simulation. Either the instance of a struct defined by the modeler must be passed via the `globals` argument to [`create_simulation`](@ref), or the individual parameters are passed using `register_global!` before [`create_model`](@ref) is called. 

A pipeable version of `register_global!` is also available, enabling the construction of a Model via a sequence of `register_*` calls. This pipeline starts with `ModelTypes()` as the source and terminates in the [`create_model`](@ref) function as the destination.
