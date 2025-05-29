```
assign_parameters!(model, collection; [options])
assign_parameters!(model; [options], param=value, ...)
```

Assign values to model parameters. New parameters can be given as key-value pairs in the function call, or in a collection, such as a `Dict`, for example.

Individual parameters can be assigned directly to the `model` using dot notation. This function should be more convenient when all parameters values are loaded from a file and available in a dictionary or some other key-value collection.

There are two options that control the behaviour.

  * `preserve_links=true` - if set to `true` new values for link-parameters are ignored and the link is updated automatically from the new values of parameters it depends on. If set to `false` any link parameters are overwritten and become non-link parameters set to the given new values.
  * `check=true` - if a parameter with the given name does not exist we ignore it. When `check` is set to `true` we issue a warning, when set to `false` we ignore it silently.

See also: [`export_parameters`](@ref) and [`export_parameters!`](@ref)

Example

```
julia> @using_example E1
julia> assign_parameters(E1.model; α=0.3, β=0.7)
```
