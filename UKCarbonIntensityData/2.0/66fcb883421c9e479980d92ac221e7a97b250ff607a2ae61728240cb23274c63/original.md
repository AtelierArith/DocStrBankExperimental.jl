```
todays_plot(; region = "")
```

Plot the 48 forecast for the carbon intensity starting from midnight on the day that the function is called. By default shows the national forecast. If the `region` kwarg is a valid region, then plot data for this region only. Valid regions are contained in [`AVAILABLE_REGIONS`](@ref).
