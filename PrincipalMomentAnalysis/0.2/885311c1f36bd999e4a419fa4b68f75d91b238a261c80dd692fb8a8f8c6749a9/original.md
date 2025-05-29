```
neighborsimplices(A::AbstractMatrix; k, r, dim, symmetric, normalizedist, groupby)
```

Create simplex graph connecting nearest neighbor samples.

# Inputs

  * `A`: Data matrix (variables × samples).
  * `k`: Number of nearest neighbors to connect. Default: `0`.
  * `r`: Connected all neighbors with disctance `≤r`. Default: `0.0`.
  * `dim`: Reduce the dimension to `dim` before computing distances. Useful to reduce noise. Default: Disabled.
  * `symmetric`: Make the simplex graph symmetric. Default: `false`.
  * `normalizedist`: Normalize distances to the scale [0.0,1.0] such that the maximal distance from a point to the origin is 0.5. Affects the `r` parameter. Default: `true`.
  * `groupby`: Only connected samples within the specified groups. Default: Disabled.

# Examples

```
julia> sg = neighborsimplices([0 0 2 2; 0 1 1 0]; k=1); sg.G
4×4 BitArray{2}:
 1  1  0  0
 1  1  0  0
 0  0  1  1
 0  0  1  1

julia> sg = neighborsimplices([0 0 2 2; 0 1 1 0]; r=0.45); sg.G
4×4 BitArray{2}:
 1  1  0  1
 1  1  1  0
 0  1  1  1
 1  0  1  1
```
