`tabular(A)` returns a LaTeX version of the two-dimensional array `A`. This function takes two optional (named) arguments:

  * `alignment` is a `String` giving the LaTeX alignment codes for the columns.   For example, if `A` is a `2`-by-`3` array, then `"cc|r"` would specify that the   first two columns are centered, then a vertical bar,   and then the third column is right justified. Default   is that all columns are `c` unless this default is changed by `set_align()`.
  * `hlines` is a `Bool` for controlling the addition of `\hline` at the end of   every row (except the last row). This is `false` by default.
