```
vcov(r::AbstractDIDResult, bys::Pair...)
```

Return a variance-covariance matrix for treatment coefficients selected based on the specified functions that return either `true` or `false`.

Depending on the argument(s) accepted by a function `f`, it is specified with argument `bys` as either `column_index => f` or `column_indices => f` where `column_index` is either a `Symbol` or `Int` for a column in [`treatcells`](@ref) and `column_indices` is an iterable collection of such indices for multiple columns. `f` is applied elementwise to each specified column to obtain a `BitVector` for selecting coefficients. If multiple `Pair`s are provided, the results are combined into one `BitVector` through bit-wise `and`.

!!! note
    This method only selects estimates for treatment coefficients. Covariates are not taken into account.

