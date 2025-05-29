```
GroupedDataFrame
```

The result of a [`groupby`](@ref) operation on an `AbstractDataFrame`; a view into the `AbstractDataFrame` grouped by rows.

Not meant to be constructed directly, see [`groupby`](@ref).

One can get the names of columns used to create `GroupedDataFrame` using the [`groupcols`](@ref) function. Similarly the [`groupindices`](@ref) function returns a vector of group indices for each row of the parent data frame.

After its creation, a `GroupedDataFrame` reflects the grouping of rows that was valid at its creation time. Therefore grouping columns of its parent data frame must not be mutated, and rows must not be added nor removed from it. To safeguard the user against such cases, if the number of rows in the parent data frame changes then trying to use `GroupedDataFrame` will throw an error. However, one can add or remove columns to the parent data frame without invalidating the `GroupedDataFrame` provided that columns used for grouping are not changed.
