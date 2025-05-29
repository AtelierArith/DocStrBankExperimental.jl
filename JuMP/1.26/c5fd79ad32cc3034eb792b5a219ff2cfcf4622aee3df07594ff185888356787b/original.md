```
@variables(model, args...)
```

Adds multiple variables to model at once, in the same fashion as the [`@variable`](@ref) macro.

The model must be the first argument, and multiple variables can be added on multiple lines wrapped in a `begin ... end` block.

The macro returns a tuple containing the variables that were defined.

## Example

```jldoctest
julia> model = Model();

julia> @variables(model, begin
           x
           y[i = 1:2] >= 0, (start = i)
           z, Bin, (start = 0, base_name = "Z")
       end)
(x, VariableRef[y[1], y[2]], Z)
```

!!! note
    Keyword arguments must be contained within parentheses (refer to the example above).

