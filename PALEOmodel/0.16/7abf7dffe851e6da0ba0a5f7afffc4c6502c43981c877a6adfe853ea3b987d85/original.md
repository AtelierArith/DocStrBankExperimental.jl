```
PlotPager(layout [, kwargs=NamedTuple()][; displayfunc=(plot, nplot)->display(plot)])
```

Accumulate plots into subplots.

`layout` is supplied to `Plots.jl` `layout` keyword, may be an Int or a Tuple (ny, nx), see [https://docs.juliaplots.org/latest/](https://docs.juliaplots.org/latest/).

Optional argument `kwargs::NamedTuple` provides additional keyword arguments passed through to `plot` (eg `(legend_background_color=nothing, )` to set all subplot legends to transparent backgrounds)

Optional keyword argument `displayfunc::(plot, nplot)->display(plot)` provides the function used to display a screen of plots, where `plot` is a Plot object and `nplot::Integer` is the sequential number of this screen.

# Usage

```
julia> pp = PlotPager((2,2))  # 4 panels per screen (2 down, 2 across)
julia> pp(plot(1:3))  # Accumulate
julia> pp(:skip, plot(1:4), plot(1:5), plot(1:6))  # add multiple panels in one command
julia> pp(:newpage) # flush any partial screen and start new page (NB: always add this at end of a sequence!)

julia> pp = PlotPager((2, 2); displayfunc=(plot, nplot)->savefig(plot, "plot_$nplot.png")) # save to file instead of default display
```

# Commands

  * `pp(p)`: accumulate plot p
  * `pp(:skip)`: leave a blank panel
  * `pp(:newpage)`: fill with blank panels and start new page
  * `pp(p1, p2, ...)`: multiple plots/commands in one call
