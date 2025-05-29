```
constraint_string(
    mode::MIME,
    ref::ConstraintRef;
    in_math_mode::Bool = false,
)
```

Return a string representation of the constraint `ref`, given the `mode`.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> @constraint(model, c, 2 * x <= 1);

julia> constraint_string(MIME("text/plain"), c)
"c : 2 x ≤ 1"
```
