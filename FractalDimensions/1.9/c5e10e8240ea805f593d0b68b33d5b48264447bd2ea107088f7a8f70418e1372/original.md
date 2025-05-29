```
LargestLinearRegion <: SlopeFit
LargestLinearRegion(; dxi::Int = 1, tol = 0.25)
```

Identify regions where the curve `y(x)` is linear, by scanning the `x`-axis every `dxi` indices sequentially (e.g. at `x[1]` to `x[5]`, `x[5]` to `x[10]`, `x[10]` to `x[15]` and so on if `dxi=5`).

If the slope (calculated via linear regression) of a region of width `dxi` is approximatelly equal to that of the previous region, within relative tolerance `tol` and absolute tolerance `0`, then these two regions belong to the same linear region.

The largest such region is then used to estimate the slope via standard linear regression of all points belonging to the largest linear region. "Largest" here means the region that covers the more extent along the `x`-axis.

Use [`linear_regions`](@ref) if you wish to obtain the decomposition into linear regions.
