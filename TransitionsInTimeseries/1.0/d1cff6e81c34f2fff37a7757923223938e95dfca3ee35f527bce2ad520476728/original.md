```
plot_indicator_changes(res) → (fig, axs)
```

Return `fig::Figure` and `axs::Matrix{Axis}`, on which `res::ChangesResults` has been visualised.

## Keyword arguments:

  * `colors = default_colors` sets the colors of the line plots that are to

be cycled through. The default correspond to the color scheme of Julia Dynamics.

  * `indicator*names = default*indicator*label(res), chametric*names =

default*chametric*label(res)`sets the labels for the indicators and the change  metrics, with the default inferring them from the names of`res.config.indicators`and`res.config.change_metrics`.

  * `accent_linewidth = 3` sets the line width for the original signals (the

surrogates have `linewidth = 1`)
