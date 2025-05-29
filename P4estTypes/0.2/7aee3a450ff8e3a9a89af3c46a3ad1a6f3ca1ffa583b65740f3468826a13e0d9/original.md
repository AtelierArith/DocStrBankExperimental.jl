```
brick(n::NTuple{3, Integer}, p::NTuple{3, Bool}=(false, false, false))
```

Returns a new [`Connectivity`](@ref) that is a rectangular `n[1]`-by-`n[2]`-by-`n[3]` octree mesh.  The brick is periodic in x, y, and z if `p[1]`, `p[2]`, and `p[3]` are `true`, respectively.
