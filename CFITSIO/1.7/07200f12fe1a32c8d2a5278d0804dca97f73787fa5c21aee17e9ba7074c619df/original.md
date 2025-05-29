```
fits_movabs_hdu(f::FITSFile, hduNum::Integer)
```

Change the current HDU to the value specified by `hduNum`, and return a symbol describing the type of the HDU.

Possible symbols are: `image_hdu`, `ascii_table`, or `binary_table`. The value of `hduNum` must range between 1 and the value returned by [`fits_get_num_hdus`](@ref).
