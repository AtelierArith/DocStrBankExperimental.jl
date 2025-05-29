```
@NLobjective(model, sense, expression)
```

Add a nonlinear objective to `model` with optimization sense `sense`. `sense` must be `Max` or `Min`.

!!! compat
    This macro is part of the legacy nonlinear interface. Consider using the new nonlinear interface documented in [Nonlinear Modeling](@ref). In most cases, you can replace `@NLobjective` with [`@objective`](@ref).


## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x)
x

julia> @NLobjective(model, Max, 2x + 1 + sin(x))

julia> print(model)
Max 2.0 * x + 1.0 + sin(x)
Subject to
```
