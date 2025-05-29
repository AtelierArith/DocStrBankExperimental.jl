```
interpolate_and_bin(
        left_bin_edges::AbstractRange{T2}, xs, ys, 
        intp::Linear, intp_grid::AbstractRange{T1}, 
         extrapolation_bc::Union{<:Real, Interpolations.BoundaryCondition}
        f::Function, args...; kwargs...) where {T1, T2}
```

Linearly interpolate the `xs` and `ys` to `intp_grid`, then bin the interpolated data  on the grid defined by the `N`-element `left_bin_edges` grid. After binning, apply  `f` with arguments `args` and keyword arguments `kwargs` element-wise to each of the bins.  Returns a vector of `N-1` bin summaries.

## Details

Binning is performed *after* interpolating `xs` and `ys` to `intp_grid`. Binning is done  by distributing the `intp_grid` values among the bins defined by `left_bin_edges`. That is,  if `intp_grid[i]` falls in the `k`-th bin, then `intp(xs)[i]` is assigned to the `k`-th bin.  If `left_bin_edges` contain `N` grid points, then there will be `N - 1` bins in total. 

If `xs` contain `NaN` values, then these are filled internally by linear interpolation  *before* interpolating to the provided `intp_grid`. 
