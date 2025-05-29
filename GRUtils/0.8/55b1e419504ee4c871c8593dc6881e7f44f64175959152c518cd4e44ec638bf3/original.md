```
shade(x, y; kwargs...)
```

Draw a point- or line-based heatmap.

The current colormap is used to display the footprint left by the pairs of `x`, `y` values. If the data contain `NaN` or `missing`, the footprints will be based on lines separated by those values. Otherwise the footprints will be based on points. The type of footprint can be enforced regardless of the input by the keyword argument `footprint = "lines"` or `footprint = "points"`.

The value of that footprint is determined by a transformation that can be adjusted by the keyword argument `xform` –- a number or a string from the following table:

|  #  | String        | description                   |
|:---:|:------------- |:----------------------------- |
|  0  | `"boolean"`   | boolean                       |
|  1  | `"linear"`    | linear                        |
|  2  | `"log"`       | logarithmic                   |
|  3  | `"loglog"`    | double logarithmic            |
|  4  | `"cubic"`     | cubic                         |
|  5  | `"equalized"` | histogram equalized (default) |

# Examples

```julia
# Create line data with NaN as polyline separator
x = [randn(10000); NaN; randn(10000) .+ 5 ]
y = [randn(10000); NaN; randn(10000) .+ 5]
# Draw shade
shade(x, y, xform="loglog")

```
