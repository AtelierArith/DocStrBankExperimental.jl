```
AvgSplit(minN, maxL)
```

Rule to be used in `RayTracer` when `acceleration = BVH`. It will divide each node along the longest axis through the mean coordinate value. The rule is parameterized by the minimum number of triangles in a leaf node (`minN`) and the maximum depth of the tree (`maxL`).

## Examples

```jldoctest
julia> rule = AvgSplit(1,5);
```
