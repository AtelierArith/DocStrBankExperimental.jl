```
bin(f::Function, left_bin_edges::AbstractRange, xs, ys, args...; kwargs...) -> Vector{T} where T
```

Distribute the elements of `ys` into `N-1` different bin vectors, based on  how the values in `xs` are distributed among the bins defined by the `N` grid  points in `left_bin_edges`. If `xs[i]` falls in the `n`-th bin interval, then `ys[i]`  is assigned to the `n`-th bin vector. If `xs[i]` lie outside the grid, then the  corresponding `ys[i]` is ignored. See also [`bin!`](@ref)

Then, apply the summary function element-wise to each of the bin vectors, with `args`  and `kwargs` as arguments and keyword arguments. Then, `N-1` summary values, one for  each bin, are returned. Empty bins are assigned `NaN` values.

Returns `N-1` bin summaries.

## Examples

### Applying a summary function to each bin

Any function that accepts a vector of values can be used in conjunction with `bin`. 

```julia
xs = [1.2, 1.7, 2.2, 3.3, 4.5, 4.6, 7.1]
ys = [4.2, 5.1, 6.5, 4.2, 3.2, 3.1, 2.5]
left_bin_edges = 0.0:1.0:6.0
bin(median, left_bin_edges, xs, ys)
```

Functions with additional arguments also work (arguments and keyword  arguments must be supplied last in the function call):

```julia
xs = [1.2, 1.7, 2.2, 3.3, 4.5, 4.6, 7.1]
ys = [4.2, 5.1, 6.5, 4.2, 3.2, 3.1, 2.5]
left_bin_edges = 0.0:1.0:6.0
bin(quantile, left_bin_edges, xs, ys, [0.1])
```
