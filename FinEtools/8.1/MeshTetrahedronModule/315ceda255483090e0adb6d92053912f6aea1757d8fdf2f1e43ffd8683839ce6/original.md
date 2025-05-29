```
T4voximg(
    img::Array{DataT,3},
    voxdims::T,
    voxval::Array{DataT,1},
) where {DataT<:Number, T}
```

Generate a tetrahedral mesh  from three-dimensional image.
