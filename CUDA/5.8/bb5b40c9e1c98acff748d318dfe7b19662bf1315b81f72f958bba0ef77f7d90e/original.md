```
CuTextureArray{T,N}(undef, dims)
```

Construct an uninitialized texture array of `N` dimensions specified in the `dims` tuple, with elements of type `T`. Use `Base.copyto!` to initialize this texture array, or use constructors that take a non-texture array to do so automatically.

!!! warning
    Experimental API. Subject to change without deprecation.

