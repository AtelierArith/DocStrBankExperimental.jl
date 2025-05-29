```
DalitzPlot # only for documentation, see example below
plot(intensity, ms)
plot(ms, intensity)
```

A plotting recipe for `DalitzPlot`.

This recipe generates a Dalitz plot as a heatmap, visualizing the intensity of a function over a specified range of invariants. The plot provides insights into the kinematic regions of a three-body decay or similar processes.

# Parameters:

  * `intensity::Function`: A real function of the invariants, `(m23², m31², m12²)`, returning the intensity at a given kinematic point.
  * `ms::MassTuple`: A tuple representing the masses of the particles involved in the system.

# Keyword Arguments:

  * `iσx`: Index of the first invariant to use for the x-axis, `1->m23²`, `2->m31²`, and `3->m12²`. Defaults to 1.
  * `iσy`: Index of the second invariant to use for the y-axis. Defaults to 2.
  * `grid_size`: The resolution of the plot grid. Higher values result in finer detail. Defaults to 100.
  * `xlims`: Limits for the x-axis in terms of the invariant range. Defaults to `lims(iσx, ms)` (calculated automatically).
  * `ylims`: Limits for the y-axis in terms of the invariant range. Defaults to `lims(iσy, ms)` (calculated automatically).

# Output:

The recipe generates:

1. A grid of invariant values for `σx` and `σy` axes.
2. A 2D array of `values`, where each element is either:

      * `NaN` if the corresponding kinematic region is forbidden by the Kibble condition.
      * The intensity calculated from the provided `intensity` function.

# Usage:

Just call a plot command, `julia plot(intensity, ms) plot(ms, intensity)``
