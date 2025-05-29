```
CuTextureArray{T,N}(undef, dims)
```

`N`-dimensional dense texture array with elements of type `T`. These arrays are optimized for texture fetching, and are only meant to be used as a source for [`CuTexture{T,N,P}`](@ref) objects.

!!! warning
    Experimental API. Subject to change without deprecation.

