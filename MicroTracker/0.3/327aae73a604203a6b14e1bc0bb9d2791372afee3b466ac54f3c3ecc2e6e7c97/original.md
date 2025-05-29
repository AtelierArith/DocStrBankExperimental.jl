```
plotannotatedframe_single(linked_data::AbstractDataFrame, particle_unique::AbstractString, framenumber::Int; showimage=true, showellipse=true, plotkwargs...)
```

Display a single frame of a video, with a single chosen microbot trajectory overlaid. Optionally, hide the fit ellipses or the image.

To plot all microbot trajectories, use [`plotannotatedframe`](@ref). `plotkwargs` are passed to `plot!()` and are intended to change the appearance of the plot.
