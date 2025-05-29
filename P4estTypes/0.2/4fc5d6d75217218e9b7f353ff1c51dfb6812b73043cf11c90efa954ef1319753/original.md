```
brick(n::NTuple{2, Integer}, p::NTuple{2, Bool}=(false, false))
```

Returns a new [`Connectivity`](@ref) that is a rectangular `n[1]`-by-`n[2]` quadtree connectivity.  The brick is periodic in x and y if `p[1]` and `p[2]` are `true`, respectively.
