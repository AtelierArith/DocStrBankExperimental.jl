```
plotlinefit(D::GMTdataset, kwargs...)
```

Plot the line fit of the points in the `D` GMTdataset type incliding confidence intervals ann error ellipses. The `D` input is the result of having run your data through the `linearfitxy` function. See its docs for the meaning of the parameters mentioned below.

  * `band_ab` or `ribbon_ab`: Plot a band, `(a±σa) + (b±σb)`, around the fitted line. `band_ab=true` uses the default  `lightblue` color. Use `band_ab=*color*` to paint it with a color of your choice (this color may include transparency)
  * `band_ci` or `ribbon_ci`: Plot a band, `(a±σa95) + (b±σb95)`, with the 95% (or other Confidence Interval). `band_ci=true`  uses the default `tomato` color. Use `band_ci=*color*` to paint it with a color of your choice (transparency included).
  * `ellipses`: optionaly plot error ellipses when the `σX,`σY` errors are known.
  * `legend`: By default we do not plot the legend boxes with line fit info. Set `legend=rue` to plot them. For the time  being the legend locations are determine automaticaly and can't be manually controlled.``
  * `lc or linecolor`: By default the fitted line is plotted with `red` color. Use `lc=*color*` to change it.
  * `lt, lw or linethickness`: By default the fitted line thickness is set to `0.5`. Use `lt=*thickness*` to change it.

Other than the above options you can use most of the `plot` options that control line and marker symbol.

# Examples:

```julia-repl
plotlinefit(D, band_ab=true, band_ci=true, legend=true, show=1)
```
