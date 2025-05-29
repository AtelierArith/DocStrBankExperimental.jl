```
exper_paramsets(userargs, df_exp, df_setup) → Vector{NamedTuple}
```

Merges `userargs` with the parameter in `df_setup` and in each row of `df_exp`

# Arguments

  * `userargs`: Arguments (e.g. as NamedTuple)
  * `df_exp::Union{Nothing, DataFrame}`: Experiment (subsets) parameter, as read from an excel file.
  * `df_setup::Union{Nothing, DataFrame}`: Experiment setup parameter, as read from an excel file.

Function `exper_paramsets` is exported.
