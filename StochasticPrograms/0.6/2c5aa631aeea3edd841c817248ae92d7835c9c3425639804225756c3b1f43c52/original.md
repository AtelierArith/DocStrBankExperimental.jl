```
delete(stochasticprogram::StochasticProgram, sp_crefs::Vector{<:SPConstraintRef}, scenario_index::Integer)
```

Delete the scenario-dependent decision constraints associated with `sp_crefs` from the `stochasticprogram` at `scenario_index`.
