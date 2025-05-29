```
list_of_constraint_types(stochasticprogram::Stochasticprogram, stage::Integer)::Vector{Tuple{Type, Type}}
```

Return a list of tuples of the form `(F, S)` where `F` is a JuMP function type and `S` is an MOI set type such that `all_constraints(stochasticprogram, stage, F, S)` returns a nonempty list.
