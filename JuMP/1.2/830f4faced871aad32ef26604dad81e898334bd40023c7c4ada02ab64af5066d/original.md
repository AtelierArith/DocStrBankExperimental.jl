```
primal_feasibility_report(
    point::Function,
    model::Model;
    atol::Float64 = 0.0,
    skip_missing::Bool = false,
)
```

A form of `primal_feasibility_report` where a function is passed as the first argument instead of a dictionary as the second argument.

## Examples

```jldoctest; setup=:(using JuMP)
julia> model = Model();

julia> @variable(model, 0.5 <= x <= 1);

julia> primal_feasibility_report(model) do v
           return value(v)
       end
Dict{Any,Float64} with 1 entry:
    x ≥ 0.5 => 0.3
```
