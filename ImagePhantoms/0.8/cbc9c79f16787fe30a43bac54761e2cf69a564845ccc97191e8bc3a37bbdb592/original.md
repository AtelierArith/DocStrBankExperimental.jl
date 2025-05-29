```
spectrum(fx::Vector, fy::Vector, fz::Vector, oa::Array{<:Object3d})
```

Return 3D k-space array sampled at grid of `(fx,fy,fz)` locations. Returned 3D array size is `length(fx) × length(fy) × length(fz)`.
