```
plotannotatedframe(linked_data::AbstractDataFrame, filename::AbstractString, framenumber::Int; showimage=true, showellipse=true, plotkwargs...)
```

Display a single frame of a video with all microbot trajectories overlaid. Optionally, hide the fit ellipses or the image.

To plot a single microbot's trajectory, use [`plotannotatedframe_single`](@ref). `plotkwargs` are passed to `plot!()` and are intended to change the appearance of the plot.
