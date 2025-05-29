```
primal_feasibility_report(
    point::Function,
    model::GenericModel{T};
    atol::T = zero(T),
    skip_missing::Bool = false,
) where {T}
```

A form of `primal_feasibility_report` where a function is passed as the first argument instead of a dictionary as the second argument.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, 0.5 <= x <= 1, start = 1.3);

julia> primal_feasibility_report(model) do v
           return start_value(v)
       end
Dict{Any, Float64} with 1 entry:
  x ≤ 1 => 0.3
```
