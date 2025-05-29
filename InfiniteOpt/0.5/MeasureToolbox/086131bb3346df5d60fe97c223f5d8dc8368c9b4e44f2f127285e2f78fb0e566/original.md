```
support_sum(expr::JuMP.AbstractJuMPScalar,
            params::Union{GeneralVariableRef, AbstractArray{GeneralVariableRef}};
            label = All
            )::GeneralVariableRef
```

Creates a measure that represents the sum of the expression over a parameter(s) using all of its supports corresponding to `label`. Also, note that it is  preferred to call [`@support_sum`](@ref) when `expr` is not just a  single variable reference.

**Example**

```julia-repl
julia> @infinite_parameter(model, x in [0, 1], supports = [0.3, 0.7])
x

julia> @variable(model, f, Infinite(x))
f(x)

julia> meas = support_sum(f, x)
support_sum{x}[f(x)]

julia> expand(meas)
f(0.3) + f(0.7)
```
