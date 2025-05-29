```
@recourse(model, expr, args..., kw_args...)
```

Add a recourse decision variable to `model` described by the expression `expr`. Replaces [`@decision`](@ref) in the [`@stage`](@ref) block of the final stage, and can only be used there. See `@variable` for syntax details.

## Examples

```julia
@recourse(model, 0 <= y <= 1)
```

See also [`@decision`](@ref), [`@parameters`](@ref), [`@uncertain`](@ref), [`@stage`](@ref)
