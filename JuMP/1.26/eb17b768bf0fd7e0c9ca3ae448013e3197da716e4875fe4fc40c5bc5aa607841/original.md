```
add_to_function_constant(constraint::ConstraintRef, value)
```

Add `value` to the function constant term of `constraint`.

Note that for scalar constraints, JuMP will aggregate all constant terms onto the right-hand side of the constraint so instead of modifying the function, the set will be translated by `-value`. For example, given a constraint `2x <= 3`, `add_to_function_constant(c, 4)` will modify it to `2x <= -1`.

## Example

For scalar constraints, the set is translated by `-value`:

```jldoctest; filter=r"≤|<="
julia> model = Model();

julia> @variable(model, x);

julia> @constraint(model, con, 0 <= 2x - 1 <= 2)
con : 2 x ∈ [1, 3]

julia> add_to_function_constant(con, 4)

julia> con
con : 2 x ∈ [-3, -1]
```

For vector constraints, the constant is added to the function:

```jldoctest; filter=r"≤|<="
julia> model = Model();

julia> @variable(model, x);

julia> @variable(model, y);

julia> @constraint(model, con, [x + y, x, y] in SecondOrderCone())
con : [x + y, x, y] ∈ MathOptInterface.SecondOrderCone(3)

julia> add_to_function_constant(con, [1, 2, 2])

julia> con
con : [x + y + 1, x + 2, y + 2] ∈ MathOptInterface.SecondOrderCone(3)
```
