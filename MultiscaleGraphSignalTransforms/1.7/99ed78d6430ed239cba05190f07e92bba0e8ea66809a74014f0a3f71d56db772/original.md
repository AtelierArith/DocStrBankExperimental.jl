```
GraphSig_Plot(G::GraphSig; symmetric::Bool = false,
  markersize::Float64 = 2.,
  markercolor::Symbol = :balance,
  markershape::Symbol = :circle,
  markerstrokewidth::Float64 = 1.0,
  markerstrokealpha::Float64 = 1.0,
  markervaluevaries::Bool = true,
  linewidth::Float64 = 1.,
  linecolor::Symbol = :blue,
  linestyle::Symbol = :solid,
  clim::Tuple{Float64,Float64} = (0., 0.),
  notitle::Bool = false, nocolorbar::Bool = false, nolegend::Bool = true,
  stemplot::Bool = false, sortnodes::Symbol = :normal)
```

Display a plot of the data in a GraphSig object

### Input Argument

  * `G::GraphSig`:        an input GraphSig object
  * `symmetric`           symmetrize the colorbar
  * `markersize`          the size of the nodes
  * `markercolor`         markercolor scheme
  * `markershape`         shape of marker
  * `markerstrokewidth`   width of marker stroke
  * `markerstrokealpha`   capacity of marker stroke
  * `markervaluevaries`   if the marker color depends on the signal value
  * `linewidth`           the width of the lines in gplot
  * `linecolor`           the color of the lines (1D) / graph edges (2D & 3D)
  * `linestyle`:          the style of line
  * `notitle`             display a title
  * `nocolorbar`          display a colorbar
  * `nolegend`            display a legend
  * `stemplot`            use a stem plot
  * `clim`                specify the dynamic display range
  * `sortnodes`           plot the signal values from smallest to largest in magnitude
