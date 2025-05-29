```
params!(out::AbstractVector, partable::ParameterTable,
              col::Symbol = :estimate)
```

Extract parameter values from the `col` column of `partable` into the `out` vector.

The `out` vector should be of `nparams(partable)` length. The *i*-th element of the `out` vector will contain the value of the *i*-th parameter from `params_labels(partable)`.

Note that the function combines the duplicate occurences of the same parameter in `partable` and will raise an error if the values do not match.
