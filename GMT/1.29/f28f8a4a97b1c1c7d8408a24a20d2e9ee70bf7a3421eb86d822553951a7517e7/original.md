```
marginalhist(data; kwargs...)
```

Takes a Mx2 array, and make a scatter plot of first vs second column. The default is to do a scatter3 plot if number of points <= 200 and bihex plot otherwise, but this is configurable.  Input `data` can be a MxN matrix, a `GMTdataset` or a file name that upon reading with `gmtread` returns a `GMTdataset`.

  * `marginalhist(data)`: Plots a *x,y* scatterplot with marginal histograms for *x* and *y*.
  * `marginalhist(..., frac|fraction=xx)`: Set fractional size of the marginal plots with respect to the  figure size. Default is 0.15 (15%).
  * `marginalhist(..., hexbin=true)`: Force hexbin plots even when number of points <= 2000.
  * `marginalhist(..., scatter=true)`: Force scatter plots even when number of points > 2000.
  * `marginalhist(..., density=true)`: Side plots contain data kernel density instead of histograms.
  * `marginalhist(..., gap=xx)`: Set the gap in centimeters between the fig and the marginal plots.
  * `marginalhist(..., histcolor|histfill=color)`: To paint the side histograms/density with  a selected color (histcolor=:none to no paint).
  * `marginalhist(..., nocbar=true)`: To not plot the color bar when doing a hexbin plot.
  * `marginalhist(..., histkw=args)`: Where `args` is a NamedTuple with parameters controlling the histogram  plot (same options as those that would be passed to the `histogram` module, except `region` and `figsize`).

Several more options in `kwargs` can be used to control plot details (and are passed to the `subplot`, `binstats` and `plot` functions.)

Example:     marginalhist(randn(2500,2), scatter=true, histkw=(annot=true,), show=true)

```
marginalhist(randn(2000,2), histkw=(frame="none", fill=:green, W="0@100"), show=true)

marginalhist(randn(2500,2), cmap=:magma, density=true, show=1)
```
