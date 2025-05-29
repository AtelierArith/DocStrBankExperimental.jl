```
CuDeviceTexture{T,N,M,NC,I}
```

`N`-dimensional device texture with elements of type `T`. This type is the device-side counterpart of [`CuTexture{T,N,P}`](@ref), and can be used to access textures using regular indexing notation. If `NC` is true, indices used by these accesses should be normalized, i.e., fall into the `[0,1)` domain. The `I` type parameter indicates the kind of interpolation that happens when indexing into this texture. The source memory of the texture is specified by the `M` parameter, either linear memory or a texture array.

Device-side texture objects cannot be created directly, but should be created host-side using [`CuTexture{T,N,P}`](@ref) and passed to the kernel as an argument.

!!! warning
    Experimental API. Subject to change without deprecation.

