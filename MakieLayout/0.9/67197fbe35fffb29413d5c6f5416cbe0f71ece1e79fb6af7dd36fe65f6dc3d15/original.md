```
LLegend(
    scene,
    contents::AbstractArray,
    labels::AbstractArray{String},
    title::Optional{String} = nothing;
    kwargs...)
```

Create a legend from `contents` and `labels` where each label is associated to one content element. A content element can be an `AbstractPlot`, an array of `AbstractPlots`, a `LegendElement`, or any other object for which the `legendelements` method is defined.
