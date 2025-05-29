```
(1) details(sem_fit::SemFit; show_fitmeasures = false)

(2) details(partable::AbstractParameterTable; ...)
```

Print information about (1) a fitted SEM or (2) a parameter table to stdout.

# Extended help

## Addition keyword arguments

  * `digits = 2`: controls precision of printed estimates, standard errors, etc.
  * `color = :light_cyan`: color of some parts of the printed output. Can be adjusted for readability.
  * `secondary_color = :light_yellow`
  * `show_variables = true`
  * `show_columns = nothing`: columns names to include in the output e.g.`[:from, :to, :estimate]`)
