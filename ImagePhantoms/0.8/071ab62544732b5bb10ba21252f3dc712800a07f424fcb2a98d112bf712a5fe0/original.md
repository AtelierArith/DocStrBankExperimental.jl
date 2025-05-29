```
image = phantom(x, y, z, oa::Array{<:Object3d}, oversample::Int; T)
```

Return a 3D digital image of the phantom sampled at grid of `(x,y,z)` locations, with over-sampling factor `oversample` and element type `T`.
