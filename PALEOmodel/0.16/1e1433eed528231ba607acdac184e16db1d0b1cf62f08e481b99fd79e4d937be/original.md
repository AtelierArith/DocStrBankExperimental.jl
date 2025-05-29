```
set_statevar_from_output!(modeldata, output::AbstractOutputWriter) -> initial_state
```

Initialize model state Variables from last record in `output`

NB: `modeldata` must contain `solver_view_all`
