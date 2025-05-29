```
ylims!(low, high)
ylims!(; low = nothing, high = nothing)
```

Set the y-axis limits of the current axis to `low` and `high`. If the limits are ordered high-low, this reverses the axis orientation. A limit set to `nothing` will be determined automatically from the plots in the axis.
