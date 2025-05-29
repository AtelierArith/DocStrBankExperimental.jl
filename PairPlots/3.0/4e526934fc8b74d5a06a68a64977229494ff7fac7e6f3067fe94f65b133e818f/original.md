```
pairplot(gridpos::Makie.GridLayout, inputs...; kwargs...)
```

Main PairPlots function. Create a pair plot by plotting into a grid layout within a Makie figure.

Inputs should be one or more `Pair` of PairPlots.AbstractSeries => tuple of VizType.

Additional arguments:

  * labels: customize the axes labels with a Dict of column name (symbol) to string, Makie rich text, or LaTeX string.
  * diagaxis: customize the Makie.Axis of plots along the diagonal with a named tuple of keyword arguments.
  * bodyaxis: customize the Makie.Axis of plots under the diagonal with a named tuple of keyword arguments.
  * axis: customize the axes by parameter using a Dict of column name (symbol) to named tuple of axis settings. `x` and `y` are automatically prepended based on the parameter and subplot.  For global properties, see `diagaxis` and `bodyaxis`.
  * legend:  additional keyword arguments to the Legend constructor, used if one or more series are labelled. You can of course also create your own Legend and inset it into the Figure for complete control.
  * fullgrid: true or false (default). Show duplicate plots above the diagonal to make a full grid.

## Examples

Basic usage:

```julia
table = (;a=randn(1000), b=randn(1000), c=randn(1000))
pairplot(table)
```

Customize labels:

```julia
pairplot(table, labels=Dict(:a=>L"\sum{a^2}"))
```

Use a pseudo log scale for one variable:

```julia
pairplot(table, axis=(; a=(;scale=Makie.pseudolog10) ))
```
