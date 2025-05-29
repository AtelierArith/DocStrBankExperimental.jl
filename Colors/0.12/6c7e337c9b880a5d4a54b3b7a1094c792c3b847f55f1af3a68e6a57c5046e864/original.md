```
colormap(cname, N=100; mid=0.5, logscale=false, kvs...])
```

Returns a predefined sequential or diverging colormap computed using the algorithm by Wijffelaars, M., et al. (2008).

Sequential colormaps `cname` choices are:

  * `Blues`
  * `Greens`
  * `Grays`
  * `Oranges`
  * `Purples`,
  * `Reds`

Diverging colormap choices are `RdBu`.

Optionally, you can specify the number of colors `N` (default 100).

Extra control is provided by keyword arguments.

  * `mid` sets the position of the midpoint for diverging colormaps.
  * `logscale=true` uses logarithmically-spaced steps in the colormap.

You can also use keyword argument names that match the argument names in [`sequential_palette`](@ref) or [`diverging_palette`](@ref).
