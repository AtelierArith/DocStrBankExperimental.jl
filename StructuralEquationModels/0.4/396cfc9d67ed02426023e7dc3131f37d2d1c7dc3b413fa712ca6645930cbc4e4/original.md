```
sort_vars!(partable::ParameterTable)
sort_vars!(partables::EnsembleParameterTable)
```

Sort variables in `partable` so that all independent variables are before the dependent variables and store it in `partable.sorted_vars`.

If the relations between the variables are acyclic, sorting will make the resulting `A` matrix in the *RAM* model lower triangular and allow faster calculations.
