```
FullSearch(d=Cityblock(), N; patch_radius, search_radius, search_stride=1)
```

Construct a block matching algorithm with full search strategy. In some literature, this is also called *exhaustive search*.

The default patch distance is `Distances.Cityblock()`.

!!! note
    If `p` is not given and if inputs are `CuArray` then GPU methods will be applied for a small set of predefined distances from Distances.jl. The result will be slightly different from its CPU version.

