```
@constraints(model, args...)
```

Adds groups of constraints at once, in the same fashion as the [`@constraint`](@ref) macro.

The model must be the first argument, and multiple constraints can be added on multiple lines wrapped in a `begin ... end` block.

The macro returns a tuple containing the constraints that were defined.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, w);

julia> @variable(model, x);

julia> @variable(model, y);

julia> @variable(model, z[1:3]);

julia> @constraints(model, begin
           x >= 1
           y - w <= 2
           sum_to_one[i=1:3], z[i] + y == 1
       end);

julia> print(model)
Feasibility
Subject to
 sum_to_one[1] : y + z[1] = 1
 sum_to_one[2] : y + z[2] = 1
 sum_to_one[3] : y + z[3] = 1
 x ≥ 1
 -w + y ≤ 2
```
