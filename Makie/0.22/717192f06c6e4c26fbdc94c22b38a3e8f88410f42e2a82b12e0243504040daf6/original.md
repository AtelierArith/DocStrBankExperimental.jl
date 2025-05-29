```
zlims!(ax, low, high)
zlims!(ax; low = nothing, high = nothing)
zlims!(ax, (low, high))
zlims!(ax, low..high)
```

Set the z-axis limits of axis `ax` to `low` and `high` or a tuple `zlims = (low,high)`. If the limits are ordered high-low, the axis orientation will be reversed. If a limit is `nothing` it will be determined automatically from the plots in the axis.
