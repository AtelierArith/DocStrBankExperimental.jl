```
coords(X; columns=nothing)
```

Reshape and filter dataframe or matrix and return the matrix in right format for unfolding.

## Parameters:

  * `X`       - the input Dataframe or matrix with the coordinates.
  * `columns` - if the input is a Dataframe with more than 3 columns, the column names of the three coordinates must be informed here (e.g. ["X","Y","Z"]).
