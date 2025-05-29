```
JuMP.add_constraint(model::InfiniteModel, c::JuMP.AbstractConstraint,
                    [name::String = ""])::InfOptConstraintRef
```

Extend `JuMP.add_constraint` to add a constraint `c` to an infinite model `model` with name `name`. Returns an appropriate constraint reference whose type depends on what variables are used to define the constraint. Errors if any  variables do not belong to `model`. This is primarily used as an internal method for the constraint macros.

**Example**

```julia-repl
julia> @infinite_parameter(model, t in [0, 10]);

julia> @variable(model, g, Infinite(t));

julia> @variable(model, x);

julia> constr = build_constraint(error, g + x, MOI.EqualTo(42));

julia> cref = add_constraint(model, constr, "name")
name : g(t) + x = 42.0, ∀ t ∈ [0, 10]
```
