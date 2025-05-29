```
plot_significance!(axs, res, signif)
```

Update the `axs::Matrix{Axis}` of a figure obtained with `plot_indicator_changes(res)` with the `signif::SurrogatesSignificance`.

## Keyword arguments:

  * `flags = nothing` provides the significance flags, for instance obtained by

thresholding the pvalues.

  * `nsurro = 20` sets the number of surrogates to plot.
