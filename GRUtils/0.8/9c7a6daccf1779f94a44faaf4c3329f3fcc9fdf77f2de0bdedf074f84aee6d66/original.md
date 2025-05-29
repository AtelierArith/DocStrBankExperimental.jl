```
xlim(inf, sup [, adjust::Bool = false])
xlim((inf, sup), ...)
ylim(inf, sup, ...)
ylim((inf, sup), ...)
zlim(inf, sup, ...)
zlim((inf, sup), ...)
```

Set the limits for the plot axes.

The axis limits can either be passed as individual arguments or as a tuple of `(inf, sup)` values. Setting either limit to `nothing` will cause it to be automatically determined based on the data, which is the default behavior.

Additionally to the limits, the flag `adjust` can be used to tell whether or not the limits have to be adjusted.

Use the keyword argument `xlim=(inf, sup)`, etc. in plotting functions, to set the axis limits during the creation of plots.

# Examples

```julia
# Set the x-axis limits to -1 and 1
xlim((-1, 1))
# Reset the x-axis limits to be determined automatically
xlim()
# Set the y-axis upper limit and set the lower limit to 0
ylim((0, nothing))
# Reset the y-axis lower limit and set the upper limit to 1
ylim((nothing, 1))
```
