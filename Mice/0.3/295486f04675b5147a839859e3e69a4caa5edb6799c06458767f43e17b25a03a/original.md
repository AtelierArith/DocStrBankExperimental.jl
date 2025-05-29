```
complete(
    mids::Mids,
    imputation::Int
    )
```

Produces a data table with missings replaced with imputed values from a multiply imputed dataset (`Mids`) object.

The Mids object must be supplied first.

The `imputation` argument is an integer identifying which specific imputation is to be used to fill in the missing values.
