```
@decision(model, expr, args..., kw_args...)
```

Add a decision variable to `model` described by the expression `expr`. If used inside a [`@stage`](@ref) block, the created variable can be used in subsequent stage blocks. [`@recourse`](@ref) should be used to mark decisions in the final stage. See `@variable` for syntax details.

## Examples

```julia
@decision(model, x >= 40)
```

See also [`@recourse`](@ref), [`@parameters`](@ref), [`@uncertain`](@ref), [`@stage`](@ref)
