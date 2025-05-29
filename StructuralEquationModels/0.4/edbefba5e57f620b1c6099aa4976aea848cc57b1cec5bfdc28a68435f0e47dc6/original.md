```
params(x::ParameterTable, col::Symbol = :estimate)
```

Extract parameter values from the `col` column of `partable`.

Returns the values vector. The *i*-th element corresponds to the value of *i*-th parameter from `params_label(partable)`.

Note that the function combines the duplicate occurences of the same parameter in `partable` and will raise an error if the values do not match.
