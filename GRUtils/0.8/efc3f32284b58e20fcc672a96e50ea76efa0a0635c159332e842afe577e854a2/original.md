```
subplot(num_rows, num_columns, indices[, replace])
```

Set a subplot in the current figure.

By default, the current plot covers the whole window. To display more than one plot, the window can be split into a number of rows and columns, with each plot covering one or more cells in the resulting grid.

Subplot indices are one-based and start at the upper left corner, with a new row starting after every `num_cols` subplots.

The arguments `num_rows` and `num_cols` indicate the number of rows and columns of the grid of plots into which the figure is meant to be divided, and `indices` is an integer or a collection of integers that identify a group of cells in that grid. This function returns a plot with the minimum size that spans over all those cells, and appends it to the array of plots of the figure, such that it becomes its current plot.

If the viewport of the new subplot coincides with the viewport of an existing plot, by default the older one is moved to the first plane, and taken as the "current plot"; but if there is only a partial overlap between the new subplot and other plots, the overlapping plots are removed. To override this behavior and keep all previous plots without changes, set the optional argument `replace` to false.

# Examples

```julia
# Create example data
x = randn(100_000)
y = randn(100_000)
# Draw an hexagonal plot in the bigger bottom-right region
subplot(3, 3, (5, 9))
hexbin(x, y, colorbar = false)
# Draw marginal histograms
subplot(3, 3, (2, 3))
histogram(x)
subplot(3, 3, (4, 7))
histogram(y, horizontal = true, xflip = true)
# Draw a shade plot in the smaller top-left region
subplot(3, 3, 1)
shade(x, y)

```
