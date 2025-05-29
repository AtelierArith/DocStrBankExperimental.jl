```
bin_mean(left_bin_edges::AbstractRange, xs, ys)
```

Distribute the elements of `ys` into `N - 1` different bin vectors, based on  how the values in `xs` are distributed among the bins defined by the `N` grid  points in `left_bin_edges`. Then compute the bin mean for each bin.

If `xs[i]` falls in the `n`-th bin interval, then `ys[i]` is assigned to the  `n`-th bin vector. If values fall outside the grid, they are ignored (if  `xs[i] < minimum(left_bin_edges)`, ignore `ys[i]`). After the `ys` values  have been assigned to bin vectors, apply the summary function `f` element-wise  to each of the bin vectors, with `args` and `kwargs` as arguments and keyword  arguments.

Returns `N - 1` mean values, one for each bin.

## Examples

```julia
xs = [1.2, 1.7, 2.2, 3.3, 4.5, 4.6, 7.1]
ys = [4.2, 5.1, 6.5, 4.2, 3.2, 3.2, 2.5]
left_bin_edges = 0.0:1.0:6.0
bin_mean(left_bin_edges, xs, ys)

# output
6-element Array{Float64,1}:
 NaN   
   4.65
   6.5 
   4.2 
   3.2 
 NaN
```
