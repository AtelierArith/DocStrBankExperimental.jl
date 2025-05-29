```
@call! model u
```

The `@call!` macro is crucial for running simulations with submodels. In the parent model's `gc` or `gd` function every one of its submodels must be called using `@call!`. Otherwise the submodels will not be updated.

Returns the output of `model` after the update. Use [`@state`](@ref) after calling `@call!` to access the new state.

# Example

```julia
function gc_parent_model(x, u, p, t; models)
    # ...
    y_child = @call! models[1] u_child
    # ...
end
```

*Note:* The `@call!` must not be used inside a dynamics (`fc` / `fd`) function. This will throw an error. If you need access to a submodels output/state inside your parent model's dynamics function use [`@out`](@ref) / [`@state`](@ref).
