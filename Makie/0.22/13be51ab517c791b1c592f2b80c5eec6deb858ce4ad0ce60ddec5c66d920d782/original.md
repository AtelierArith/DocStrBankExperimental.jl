```
Legend(
    fig_or_scene,
    contentgroups::AbstractVector{<:AbstractVector},
    labelgroups::AbstractVector{<:AbstractVector},
    titles::AbstractVector;
    kwargs...)
```

Create a multi-group legend from `contentgroups`, `labelgroups` and `titles`. Each group from `contentgroups` and `labelgroups` is associated with one title from `titles` (a title can be `nothing` to hide it).

Within each group, each content element is associated with one label. A content element can be an `AbstractPlot`, an array of `AbstractPlots`, a `LegendElement`, or any other object for which the `legendelements` method is defined.
