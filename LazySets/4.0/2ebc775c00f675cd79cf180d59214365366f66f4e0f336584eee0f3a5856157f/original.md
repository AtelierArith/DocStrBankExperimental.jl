```
forget_sets!(cms::CachedMinkowskiSumArray)
```

Tell a cached Minkowski sum to forget the stored sets (but not the support vectors). Only those sets are forgotten for which a support vector has been computed in each of the cached directions.

### Input

  * `cms` – cached Minkowski sum

### Output

The number of sets that have been forgotten.

### Notes

This function should only be used under the assertion that no new directions are queried in the future; otherwise such support-vector results will be incorrect.

This implementation is optimistic and first tries to remove all sets. However, it also checks that for all cached directions the support vector has been computed before. If it finds that this is not the case, the implementation identifies the biggest index $k$ such that the above holds for the $k$ oldest sets, and then it only removes these. See the example below.

### Examples

```jldoctest
julia> x1 = BallInf(ones(3), 3.); x2 = Ball1(ones(3), 5.);

julia> cms1 = CachedMinkowskiSumArray(2); cms2 = CachedMinkowskiSumArray(2);

julia> d = ones(3);

julia> a1 = array(cms1); a2 = array(cms2);

julia> push!(a1, x1); push!(a2, x1);

julia> σ(d, cms1); σ(d, cms2);

julia> push!(a1, x2); push!(a2, x2);

julia> σ(d, cms1);

julia> idx1 = forget_sets!(cms1) # support vector was computed for both sets
2

julia> idx1 = forget_sets!(cms2) # support vector was only computed for first set
1
```
