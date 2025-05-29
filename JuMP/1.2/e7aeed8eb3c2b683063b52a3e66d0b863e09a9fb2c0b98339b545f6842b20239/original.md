```
relax_integrality(model::Model)
```

Modifies `model` to "relax" all binary and integrality constraints on variables. Specifically,

  * Binary constraints are deleted, and variable bounds are tightened if necessary to ensure the variable is constrained to the interval $[0, 1]$.
  * Integrality constraints are deleted without modifying variable bounds.
  * An error is thrown if semi-continuous or semi-integer constraints are present (support may be added for these in the future).
  * All other constraints are ignored (left in place). This includes discrete constraints like SOS and indicator constraints.

Returns a function that can be called without any arguments to restore the original model. The behavior of this function is undefined if additional changes are made to the affected variables in the meantime.

# Example

```jldoctest; setup=:(using JuMP)
julia> model = Model();

julia> @variable(model, x, Bin);

julia> @variable(model, 1 <= y <= 10, Int);

julia> @objective(model, Min, x + y);

julia> undo_relax = relax_integrality(model);

julia> print(model)
Min x + y
Subject to
 x ≥ 0.0
 y ≥ 1.0
 x ≤ 1.0
 y ≤ 10.0

julia> undo_relax()

julia> print(model)
Min x + y
Subject to
 y ≥ 1.0
 y ≤ 10.0
 y integer
 x binary
```
