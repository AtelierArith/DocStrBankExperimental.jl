```
CuTexture{T,N,P}
```

`N`-dimensional texture object with elements of type `T`. These objects do not store data themselves, but are bounds to another source of device memory. Texture objects can be passed to CUDA kernels, where they will be accessible through the [`CuDeviceTexture`](@ref) type.

!!! warning
    Experimental API. Subject to change without deprecation.

