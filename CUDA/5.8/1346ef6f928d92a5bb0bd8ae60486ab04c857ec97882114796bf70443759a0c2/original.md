```
CuTexture(x::CuArray{T,N})
```

Create a `N`-dimensional texture object that reads from a `CuArray`.

Note that it is necessary the their memory is well aligned and strided (good pitch). Currently, that is not being enforced.

!!! warning
    Experimental API. Subject to change without deprecation.

