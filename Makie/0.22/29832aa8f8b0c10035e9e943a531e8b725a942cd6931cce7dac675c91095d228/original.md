```
xlims!(ax, low, high)
xlims!(ax; low = nothing, high = nothing)
xlims!(ax, (low, high))
xlims!(ax, low..high)
```

Set the x-axis limits of axis `ax` to `low` and `high` or a tuple `xlims = (low,high)`. If the limits are ordered high-low, the axis orientation will be reversed. If a limit is `nothing` it will be determined automatically from the plots in the axis.
