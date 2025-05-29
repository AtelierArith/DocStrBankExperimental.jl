```
minimap(grd; central_longitude=200°)
```

Plots a surface map of grd with no ticks, labels, or colorbar.

The goal of this function is to provide a way to plot both a minimap and a cruise track when plotting a transect:

```
plottransect(dummy, grd; ct=sort(ct))
plot!(inset_subplots=bbox(0.73,0.73,0.15,0.15), subplot=2)
minimap!(grd; subplot=2)
plotcruisetrack!(sort(ct), subplot=2)
```
