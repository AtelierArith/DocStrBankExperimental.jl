```
plotmap(m::OpenStreetMapX.MapData;
    roadwayStyle = OpenStreetMapXPlot.LAYER_STANDARD,
    width::Integer=600, height::Integer=600, use_plain_pyplot::Bool=false)
```

Plots `roadways` for a given map `m`.

The width will be set to `width` and the height will be set to `height`. If only one of `width` or `height` is set, the other will be set to perserve the aspect ratio of the bounding box. The `km` parameter can be used to have a kilometer scale of the map instead of meters.

The default plotting backend is whatever is defined in `Plots.jl`, however if the `use_plain_pyplot` is set to `true` Plots.pythonplot() will be called to switch to PythonPlot backend (note this option is depraciated and normally backend should be changed outside of this function).

Returns an object that can be used for further plot updates.
