```
interactive_poincaresos(cds, plane, idxs, complete; kwargs...)
```

Launch an interactive application for exploring a Poincaré surface of section (PSOS) of the continuous dynamical system `cds`. Requires `DynamicalSystems`.

The `plane` can only be the `Tuple` type accepted by `DynamicalSystems.poincaresos`, i.e. `(i, r)` for the `i`th variable crossing the value `r`. `idxs` gives the two indices of the variables to be displayed, since the PSOS plot is always a 2D scatterplot. I.e. `idxs = (1, 2)` will plot the 1st versus 2nd variable of the PSOS. It follows that `plane[1] ∉ idxs` must be true.

`complete` is a three-argument **function** that completes the new initial state during interactive use, see below.

The function returns: `figure, laststate` with the latter being an observable containing the latest initial `state`.

## Keyword Arguments

  * `direction, rootkw` : Same use as in `DynamicalSystems.poincaresos`.
  * `tfinal = (1000.0, 10.0^4)` : A 2-element tuple for the range of values for the total integration time (chosen interactively).
  * `color` : A **function** of the system's initial condition, that returns a color to plot the new points with. The color must be `RGBf/RGBAf`.  A random color is chosen by default.
  * `labels = ("u₁" , "u₂")` : Scatter plot labels.
  * `scatterkwargs = ()`: Named tuple of keywords passed to `scatter`.
  * `diffeq = NamedTuple()` : Any extra keyword arguments are passed into `init` of DiffEq.

## Interaction

The application is a standard scatterplot, which shows the PSOS of the system, initially using the system's `u0`. Two sliders control the total evolution time and the size of the marker points (which is always in pixels).

Upon clicking within the bounds of the scatter plot your click is transformed into a new initial condition, which is further evolved and its PSOS is computed and then plotted into the scatter plot.

Your click is transformed into a full `D`-dimensional initial condition through the function `complete`. The first two arguments of the function are the positions of the click on the PSOS. The third argument is the value of the variable the PSOS is defined on. To be more exact, this is how the function is called:

```julia
x, y = mouseclick; z = plane[2]
newstate = complete(x, y, z)
```

The `complete` function can throw an error for ill-conditioned `x, y, z`. This will be properly handled instead of breaking the application. This `newstate` is also given to the function `color` that gets a new color for the new points.
