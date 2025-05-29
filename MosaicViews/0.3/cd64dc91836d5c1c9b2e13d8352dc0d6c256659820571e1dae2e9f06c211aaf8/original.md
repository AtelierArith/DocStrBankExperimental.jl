```
mosaic(A1, A2...; center=true, kwargs...)
mosaic([A1, A2, ...]; center=true, kwargs...)
```

Create a mosaic out of input arrays `A1`, `A2`, .... `mosaic` is essentially a more flexible version of `cat` or `hvcat`; like them it makes a copy of the inputs rather than returning a "view."

If `center` is set to `true`, then the padded arrays will be shifted to the center; if set to false, they shift to the top-left corner. This parameter is only useful when arrays are of different sizes.

All the keyword arguments of [`mosaicview`](@ref) are also supported.
