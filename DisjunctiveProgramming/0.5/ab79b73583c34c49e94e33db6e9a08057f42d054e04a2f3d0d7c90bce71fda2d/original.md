```
Disjunct
```

Used as a tag for constraints that will be used in disjunctions. This is done via  the following syntax:

```julia-repl
julia> @constraint(model, [constr_expr], Disjunct)

julia> @constraint(model, [constr_expr], Disjunct(lvref))
```

where `lvref` is a [`LogicalVariableRef`](@ref) that will ultimately be associated  with the disjunct the constraint is added to. If no `lvref` is given, then one is  generated when the disjunction is created.
