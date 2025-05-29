```
onpick(f, scene::SceneLike, plots::AbstractPlot...)
```

Calls `f(idx)` whenever the mouse is over any of `plots`. `idx` is an index, e.g. when over a scatter plot, it will be the index of the hovered element
