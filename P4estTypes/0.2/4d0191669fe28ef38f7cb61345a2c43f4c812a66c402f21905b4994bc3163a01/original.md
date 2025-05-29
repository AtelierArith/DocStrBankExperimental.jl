```
brick(l, m, n, p=false, q=false, r=false)
```

Returns a new [`Connectivity`](@ref) that is a rectangular `l`-by-`m`-by-`n` octree mesh.  The brick is periodic in x, y, and z if `p`, `q`, and `r` are `true`, respectively.
