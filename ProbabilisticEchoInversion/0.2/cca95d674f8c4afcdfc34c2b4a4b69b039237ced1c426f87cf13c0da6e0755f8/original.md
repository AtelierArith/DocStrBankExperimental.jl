```
unstack_echogram(echo_df, xcol, ycol, fcol, svcol[, X, Y, F])
```

Convert a long-format `DataFrame` of multifrequency acoustic data into a three-dimensional `DimArray` representing an echogram. This `DataFrame` must contain the following columns:

1. An x-coordinate, such as along-track distance or time
2. A y-coordinate, such as depth or range from the transducer
3. Acoustic frequency, and
4. Acoustic mean volume backscatter (can be in linear or decibel units )

The names of these columns are passed to `unstack_echogram` as the second through fifth arguments, respectively.

  * `echo_df::DataFrame` : Long-format `DataFrame` with columns for an x and y coordinate,

acoustic frequency, and backscatter.

  * `xcol`, `ycol`, `fcol`, `svcol` : Names of the columns in `echo_df` (as `Symbol`s)
  * `X`, `Y`, `F` : Optional `Dimensions` to apply to the x, y, and frequency axes of the

resulting `DimArray`.
