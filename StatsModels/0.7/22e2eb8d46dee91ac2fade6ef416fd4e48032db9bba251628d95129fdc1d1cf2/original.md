```
    lag(term, nsteps::Integer)

This `@formula` term is used to introduce lagged variables.
For example `lag(x,1)` effectively adds a new column containing
the value of the `x` column from the previous row.
If there is no such row (e.g. because this is the first row),
then the lagged column will contain `missing` for that entry.

Note: this is only a basic row-wise lag operation.
It is up to the user to ensure that data is sorted by the temporal variable,
and that observations are spaced with regular time-steps.
(Which may require adding extra-rows filled with `missing` values.)
```
