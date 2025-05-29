```
corrplot
```

This plot type shows the correlation among input variables.   A correlation plot may be produced by a matrix.

A correlation matrix can also be created from the columns of a `DataFrame` using the [`@df`](@ref) macro like so:

```julia
@df iris corrplot([:SepalLength :SepalWidth :PetalLength :PetalWidth])
```

The marker color in scatter plots reveals the degree of correlation.  Pass the desired colorgradient to `markercolor`.

With the default gradient positive correlations are blue, neutral are yellow  and negative are red. In the 2d-histograms, the color gradient shows the frequency  of points in that bin (as usual, controlled by `seriescolor`).
