```
linear_region(x, y; kwargs...) -> (region, slope)
```

Call [`linear_regions`](@ref) and identify and return the largest linear region (a `UnitRange` of the indices of `x`) and its corresponding slope.

The keywords `dxi, tol` are propagated as-is to [`linear_regions`](@ref). The keyword `ignore_saturation = true` ignores saturation that (sometimes) happens at the start and end of the curve `y(x)`, where the curve flattens. The keyword `sat = 0.01` decides what saturation is (while `abs(y[i]-y[i+1])<sat` we are in a saturation regime).

The keyword `warning = true` prints a warning if the linear region is less than 1/3 of the available x-axis.
