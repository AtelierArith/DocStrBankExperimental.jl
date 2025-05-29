```
@state model
```

Returns the current state of `model`. This macro is useful in `fc` or `fd` functions when access to a submodel's state is needed. The macro works similar to [`@out`](@ref).

**Note:** `@state` does not update the `model`. It only returns its current state. Use [`@call!`](@ref) to update submodels.

# Example

```julia
function fc_parent_model(x, u, p, t; models)
    x_child = @state models[1]
    # ...
end
```
