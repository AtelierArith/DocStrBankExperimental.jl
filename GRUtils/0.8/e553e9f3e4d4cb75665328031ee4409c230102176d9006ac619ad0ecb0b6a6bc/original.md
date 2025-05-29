```
legend(labels...; kwargs...)
```

Set the legend of the plot, using a series of `labels` (strings).

In addition to the legend strings, the keyword argument `location` can be used to define the location of the legend with respect to the plot axes and the keyword argument `maxrows` to distribute the legend labels in a grid with a maximum number of rows.

Locations are defined as a number or a string, as indicated in the following table –- based on the convention of [Matplotlib legends](https://matplotlib.org/3.1.1/api/_as_gen/matplotlib.pyplot.legend.html):

|  ⁣# | String                 |
| ---:|:---------------------- |
|   0 | `"none"`               |
|   1 | `"upper right"`        |
|   2 | `"upper left"`         |
|   3 | `"lower left"`         |
|   4 | `"lower right"`        |
|   5 | `"right"`              |
|   6 | `"center left"`        |
|   7 | `"center right"`       |
|   8 | `"lower center"`       |
|   9 | `"upper center"`       |
|  10 | `"center"`             |
|  11 | `"outer upper right"`  |
|  12 | `"outer center right"` |
|  13 | `"outer lower right"`  |

The labels are assigned to the geometries contained in the plot, in the same order as they were created. The assignment can be restricted to specific kinds of geometries through the keyword argument `kinds`, which can take a `Symbol` or a collection of `Symbol`s that identify the kinds. Use the helper function [`geometrykinds`](@ref) to see the list of kinds available in the current plot.

Only geometries with non-empty labels and an available guide for legends will be presented in the legend.

# Examples

```julia
# Set the legends to "a" and "b"
legend("a", "b")
```
