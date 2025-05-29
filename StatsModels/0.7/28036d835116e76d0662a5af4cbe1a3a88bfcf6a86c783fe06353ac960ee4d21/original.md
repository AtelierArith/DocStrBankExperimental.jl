```
    lead(term, nsteps::Integer)

This `@formula` term is used to introduce lead variables.
For example `lead(x,1)` effectively adds a new column containing
the value of the `x` column from the next row.
If there is no such row (e.g. because this is the last row),
then the lead column will contain `missing` for that entry.

Note: this is only a basic row-wise lead operation.
It is up to the user to ensure that data is sorted by the temporal variable,
and that observations are spaced with regular time-steps.
(Which may require adding extra-rows filled with `missing` values.)
```
