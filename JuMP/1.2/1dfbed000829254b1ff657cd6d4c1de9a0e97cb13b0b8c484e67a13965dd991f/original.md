```
VariableRef(c::ConstraintRef)
```

Get the variable associated with a `ConstraintRef`, if `c` is a constraint on a single variable.

## Examples

```jldoctest
julia> model = Model();

julia> @variable(model, x >= 0)
x

julia> c = LowerBoundRef(x)
x ≥ 0.0

julia> VariableRef(c) == x
true
```
