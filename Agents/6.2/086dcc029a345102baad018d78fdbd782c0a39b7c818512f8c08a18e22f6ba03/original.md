```
abmexploration(model::ABM; alabels, mlabels, kwargs...)
```

Open an interactive application for exploring an agent based model and the impact of changing parameters on the time evolution. Requires `Agents`.

The application evolves an ABM interactively and plots its evolution, while allowing changing any of the model parameters interactively and also showing the evolution of collected data over time (if any are asked for, see below). The agent based model is plotted and animated exactly as in [`abmplot`](@ref), and the `model` argument as well as splatted `kwargs` are propagated there as-is. This convencience function *only works for aggregated agent data*.

Calling `abmexploration` returns: `fig::Figure, abmobs::ABMObservable`. So you can save and/or further modify the figure and it is also possible to access the collected data (if any) via the `ABMObservable`.

Clicking the "reset" button will add a red vertical line to the data plots for visual guidance.

## Keywords arguments (in addition to those in `abmplot`)

  * `alabels, mlabels`: If data are collected from agents or the model with `adata, mdata`, the corresponding plots' y-labels are automatically named after the collected data. It is also possible to provide `alabels, mlabels` (vectors of strings with exactly same length as `adata, mdata`), and these labels will be used instead.
  * `figure = NamedTuple()`: Keywords to customize the created Figure.
  * `axis = NamedTuple()`: Keywords to customize the created Axis.
  * `plotkwargs = NamedTuple()`: Keywords to customize the styling of the resulting [`scatterlines`](https://makie.juliaplots.org/dev/examples/plotting_functions/scatterlines/index.html) plots.
