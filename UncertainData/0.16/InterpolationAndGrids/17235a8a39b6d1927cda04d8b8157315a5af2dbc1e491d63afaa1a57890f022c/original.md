```
bin(left_bin_edges::AbstractRange, xs, ys) -> Vector{Vector{T}} where T
```

Distribute the elements of `ys` into `N-1` different bin vectors, based on  how the values in `xs` are distributed among the bins defined by the `N` grid  points in `left_bin_edges`. If `xs[i]` falls in the `n`-th bin interval, then `ys[i]`  is assigned to the `n`-th bin vector. If `xs[i]` lie outside the grid, then the  corresponding `ys[i]` is ignored. See also [`bin!`](@ref)

Returns `N - 1` bin vectors.

## Examples

### Getting the values in each bin:

```julia
xs = [1.2, 1.7, 2.2, 3.3, 4.5, 4.6, 7.1]
ys = [4.2, 5.1, 6.5, 4.2, 3.2, 3.1, 2.5]
left_bin_edges = 0.0:1.0:6.0
bin(left_bin_edges, xs, ys)
```

```julia
# Some example data with unevenly spaced time indices
npts = 300
time, vals = sort(rand(1:1000, npts)), rand(npts)

# See which values fall in 25 time step wide time bins ranging 
# from time indices 100 to 900.
left_bin_edges = 100:25:900

bin(left_bin_edges, time, vals)
```
