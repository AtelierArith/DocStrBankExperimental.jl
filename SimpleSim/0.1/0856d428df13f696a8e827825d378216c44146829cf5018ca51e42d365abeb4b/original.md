```
@out model
```

Returns the current output of `model`. This macro is useful in `fc` or `fd` functions when access to a submodel's output is needed. The macro works similar to [`@state`](@ref).

# Example

```julia
function fc_parent_model(x, u, p, t; models)
    y_child = @out models[1]
    # ...
end
```

**Note:** `@out` does not update the `model`. It only returns its current output. Use [`@call!`](@ref) to update submodels.
