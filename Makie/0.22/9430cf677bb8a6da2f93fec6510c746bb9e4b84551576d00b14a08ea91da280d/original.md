```
ylims!(ax, low, high)
ylims!(ax; low = nothing, high = nothing)
ylims!(ax, (low, high))
ylims!(ax, low..high)
```

Set the y-axis limits of axis `ax` to `low` and `high` or a tuple `ylims = (low,high)`. If the limits are ordered high-low, the axis orientation will be reversed. If a limit is `nothing` it will be determined automatically from the plots in the axis.
