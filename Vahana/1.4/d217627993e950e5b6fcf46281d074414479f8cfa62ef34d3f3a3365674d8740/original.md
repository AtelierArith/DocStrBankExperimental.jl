```
register_param!(types::ModelTypes, name::Symbol, default_value::T)
```

There are two ways to set up parameters for a simulation. Either the instance of a struct defined by the modeler must be passed via the `param` argument to [`create_simulation`](@ref), or the individual parameters are passed using `register_param!` before [`create_model`](@ref) is called. The parameters can also be set after [`create_simulation`](@ref) and before [`finish_init!`](@ref) is called.

A pipeable version of `register_param!` is also available, enabling the construction of a Model via a sequence of `register_*` calls. This pipeline starts with `ModelTypes()` as the source and terminates in the [`create_model`](@ref) function as the destination.
