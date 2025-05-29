```
interactive_cobweb(ds::DiscreteDynamicalSystem, prange, O::Int = 3; kwargs...)
```

Launch an interactive application for exploring cobweb diagrams of 1D discrete dynamical systems. Two slides control the length of the plotted trajectory and the current parameter value. The parameter values are obtained from the given `prange`.

In the cobweb plot, higher order iterates of the dynamic rule `f` are plotted as well, starting from order 1 all the way to the given order `O`. Both the trajectory in the cobweb, as well as any iterate `f` can be turned off by using some of the buttons.

## Keywords

  * `fkwargs = [(linewidth = 4.0, color = randomcolor()) for i in 1:O]`: plotting keywords for each of the plotted iterates of `f`
  * `trajcolor = :black`: color of the trajectory
  * `pname = "p"`: name of the parameter slider
  * `pindex = 1`: parameter index
  * `xmin = 0, xmax = 1`: limits the state of the dynamical system can take
  * `Tmax = 1000`: maximum trajectory length
  * `x0s = range(xmin, xmax; length = 101)`: Possible values for the x0 slider.
