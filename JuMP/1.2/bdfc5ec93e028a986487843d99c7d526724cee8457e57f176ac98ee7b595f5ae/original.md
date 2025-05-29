```
unregister(model::Model, key::Symbol)
```

Unregister the name `key` from `model` so that a new variable, constraint, or expression can be created with the same key.

Note that this will not delete the object `model[key]`; it will just remove the reference at `model[key]`. To delete the object, use

```julia
delete(model, model[key])
unregister(model, key)
```

See also: [`object_dictionary`](@ref).

## Examples

```jldoctest; setup=:(model = Model())
julia> @variable(model, x)
x

julia> @variable(model, x)
ERROR: An object of name x is already attached to this model. If
this is intended, consider using the anonymous construction syntax,
e.g., `x = @variable(model, [1:N], ...)` where the name of the object
does not appear inside the macro.

Alternatively, use `unregister(model, :x)` to first unregister the
existing name from the model. Note that this will not delete the object;
it will just remove the reference at `model[:x]`.
[...]

julia> num_variables(model)
1

julia> unregister(model, :x)

julia> @variable(model, x)
x

julia> num_variables(model)
2
```
