```
SAH{K}(minN, maxL)
```

Rule to be used in `RayTracer` when `acceleration = BVH`. It will divide each node at the axis and location using the Surface Area Heuristics. To speed up the construction, only `K` cuts will be tested per axis. These cuts will correspond to the quantiles along each axis. The rule is parameterized by the minimum number of triangles in a leaf node (`minN`) and the maximum depth of the tree (`maxL`).

## Examples

```jldoctest
julia> rule = SAH{3}(1,5);
```
