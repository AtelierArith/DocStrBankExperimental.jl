```
pairplot(gridpos::Makie.GridLayout, inputs...; kwargs...)
```

Convenience function to create a reasonable pair plot given one or more inputs that aren't full specified. Wraps input tables in PairPlots.Series() with a distinct color specified for each series.

Here are the defaults applied for a single data table:

```julia
pairplot(fig[1,1], table) == # approximately the following:
pairplot(
    PairPlots.Series(table, color=Makie.RGBA(0., 0., 0., 0.5)) => (
        PairPlots.HexBin(colormap=Makie.cgrad([:transparent, :black]),),
        PairPlots.Scatter(filtersigma=2),
        PairPlots.Contour(),
        PairPlots.MarginDensity(
            color=:transparent,
            color=:black,
            linewidth=1.5f0
        ),
        PairPlots.MarginQuantileText()
    )
)
```

Here are the defaults applied for 2 to 5 data tables:

```julia
pairplot(fig[1,1], table1, table2) == # approximately the following:
pairplot(
    PairPlots.Series(table1, color=Makie.wong_colors(0.5)[1]) => (
        PairPlots.Scatter(filtersigma=2),
        PairPlots.Contourf(),
        PairPlots.MarginDensity(
            linewidth=2.5f0
        )
    ),
    PairPlots.Series(table2, color=Makie.wong_colors(0.5)[2]) => (
        PairPlots.Scatter(filtersigma=2),
        PairPlots.Contourf(),
        PairPlots.MarginDensity(
            linewidth=2.5f0
        )
    ),
)
```

For 6 or more tables, the defaults are approximately:

```julia
PairPlots.Series(table1, color=Makie.wong_colors(0.5)[series_i]) => (
    PairPlots.Contour(sigmas=[1]),
    PairPlots.MarginDensity(
        linewidth=2.5f0
    )
)
```
