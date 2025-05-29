```
parallelplot(cmd0="", arg1=nothing; labels|axeslabels=String[], group=Vector{String},
             groupvar="", normalize="range", kwargs...)
```

  * `axeslabels` or `labels`: String vector with the names of each variable axis. Plots a default "Label?" if    not provided.
  * `group`: A string vector or vector of integers used to group the lines in the plot.
  * `groupvar`: Uses the table variable specified by `groupvar` to group the lines in the plot. `groupvar` can    be a column number, or a column name passed in as a Symbol. *e.g.* `groupvar=:Male` if a column with that    name exists.  When `arg1` is GMTdatset or `cmd0` is the name of a file with one and it has the `text` field    filled, use `groupvar="text"` to use that text field as the grouping vector.
  * `yvar`: This can take the form of column names or column numbers. Example `yvar=(2,3)`, or `yvar=[:Y, :Z1, :Z2]`.
  * `nomalize`: 

      * `range`: (Default) Display raw data along coordinate rulers that have independent minimum and maximum limits.

```
- `none`: Display raw data along coordinate rulers that have the same minimum and maximum limits.
- `zscore`: Display z-scores (with a mean of 0 and a standard deviation of 1) along each coordinate ruler.
- `scale`: Display values scaled by standard deviation along each coordinate ruler.
```

  * `quantile`: Give a quantile in the [0-1] interval to plot the median +- `quantile` as dashed lines.
  * `std`: Instead of median plus quantile lines, draw the mean +- one standard deviation. This is achieved with    both `std=true` or `std=1`. For other number od standard deviations use, *e.g.* `std=2`, or `std=1.5`.
  * `band`: If used, instead of the dashed lines referred above, plot a band centered in the median. The band    colors are assigned automatically but this can be overriden by the `fill` option. If set and `quantile`    not given, set a default of `quantile = 0.25`.
  * `fill`: When `band` option is used and want to control the bands colors, give a list of colors to paint them.
  * `fillalpha` : When `fill` option is used, we can set the bands transparency with this option that takes in an array   (vec or 1-row matrix) with numeric values between [0-1] or ]1-100], where 100 (or 1) means full transparency.
  * For fine the lines settings use the same options as in the `plot` module.

Example:

```
parallelplot("iris.dat", groupvar="text", quantile=0.25, legend=true, band=true, show=1)
```
