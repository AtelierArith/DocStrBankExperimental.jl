```
add_method_initialize_zero_vars_default!(react::AbstractReaction, variables=PB.get_variables(react))
```

Create and add a default method to initialize Variables to zero at beginning of each timestep. Defaults to adding all Variables from `react` with `:initialize_to_zero` attribute `true`.

NB: TODO variables are converted to VarDep (no dependency checking or sorting needed, could define a VarInit or similar?)
