```
detect_wada_merge_method(xg,yg, basin)
```

The algorithm gives the maximum and minimum Haussdorff distances between merged basins. These two distances can help to decide if the basin has the Wada property.

[A. Daza, A. Wagemakers and M. A. F. Sanjuán, Ascertaining when a basin is Wada: the merging method, Sci. Rep., 8, 9954 (2018)]

## Arguments

  * `basin` : the matrix containing the information of the basin.
  * `xg`, `yg` : 1-dim range vector that defines the grid of the initial conditions to test.

## Example

```
max_dist,min_dist = detect_wada_merge_method(basin,xg,yg)
# grid resolution
epsilon = xg[2]-xg[1]
# if dmax is large then this is not Wada
@show dmax = max_dist/epsilon
@show dmin = min_dist/epsilon
```
