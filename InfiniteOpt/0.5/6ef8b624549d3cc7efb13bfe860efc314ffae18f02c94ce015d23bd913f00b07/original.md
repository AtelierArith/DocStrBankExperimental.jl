```
JuMP.relax_integrality(model::InfiniteModel)::Function
```

Modifies `model` to "relax" all binary and integrality constraints on variables. Specifically,

  * Binary constraints are deleted, and variable bounds are tightened if necessary to ensure the variable is constrained to the interval $[0, 1]$.
  * Integrality constraints are deleted without modifying variable bounds.
  * All other constraints are ignored (left in place). This includes discrete constraints like SOS and indicator constraints.

Returns a function that can be called without any arguments to restore the original model. The behavior of this function is undefined if additional changes are made to the affected variables in the meantime.

**Example**

```julia-repl
julia> undo_relax = relax_integrality(model);

julia> print(model)
Min x + ∫{t ∈ [0, 10]}(y(t))
Subject to
 x ≥ 0.0
 y(t) ≥ 1.0
 x ≤ 1.0
 y(t) ≤ 10.0

julia> undo_relax()

julia> print(model)
Min x + ∫{t ∈ [0, 10]}(y(t))
Subject to
 y(t) ≥ 1.0
 y(t) ≤ 10.0
 y(t) integer
 x binary
```
