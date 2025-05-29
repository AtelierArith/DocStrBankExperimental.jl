```
vowelplot(f1, f2, cats; meansOnly=false, addLabels=true, ell=false, ellPercent=0.67, nEllPts=500, kw...)
```

Create an F1-by-F2 vowel plot. The `f1` values are displayed along the x-axis, and the `f2` values are displayed along the y-axis, with each unique vowel class in `cats` being represented with a new color. The series labels in the legend will take on the unique values contained in `cats`. The alternate display whereby reversed F2 is on the x-axis and reversed F1 is on the y-axis can be created by passing the F2 values in for the `f1` argument and F1 values in for the `f2` argument, and then using the `:flip` magic argument provided by the `Plots` package.

If `meansOnly` is set to true, only the mean values for each vowel category are plotted. Using `ell=true` will plot a data ellipse that approximately encompases the percentage of data specified by `ellPercent`. The ellipse is represented by a number of points specified with `nEllPts`. Other arguments to `plot` are passed in through the splatted `kw` argument. Setting the `addLabels` argument to `true` will add the text label of the vowel category above and to the right of the mean.

Argument structure inferred from using plot recipe. Parameters such as `xlim`, `ylim`, `color`, and `size` should be passed as keyword arguments, as with standard calls to `plot`. Plot parameters `markersize` defaults to `3` and `linewidth` defaults to 3.

# Args

  * `f1` The F1 values, or otherwise the values to plot on the x-axis
  * `f2` The F2 values, or otherwise the values to plot on the y-axis
  * `cats` The vowel categories associated with each F1, F2 pair
  * `meansOnly` Plot only mean value for each category
  * `addLabels` Add labels for each category to the plot near the mean
  * `ell` Whether to add data ellipses to the plot
  * `ellPercent` Percentage of the data distribution the ellipse should cover (approximately)
  * `nEllPts` How many points should be used when plotting the ellipse
