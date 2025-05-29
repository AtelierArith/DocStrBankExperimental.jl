```
xlog(flag)
ylog(flag)
zlog(flag)
```

Set the X-, Y- or Z-axis to be drawn in logarithmic scale (`flag == true`), or in linear scale (`flag == false`).

Use the keyword argument `xlog=<true/false>`, etc. in plotting functions, to set the logarithmic axes during the creation of plots.

!!! note
    When the axis is set to logarithmic scale, its lower limit is adjusted to represent only positive values, even if the data of the plot contain zero or negative values. The aspect of logarithmic axes with limits explicitly set to contain negative values (with [`xlim`](@ref), etc.) is undefined.


# Examples

```julia
# Set the x-axis limits to log scale
xlog(true)
# Ensure that the y-axis is in linear scale
ylog(false)
```
