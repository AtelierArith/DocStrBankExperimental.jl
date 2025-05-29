```
fits_delete_hdu(f::FITSFile)
```

Delete the HDU from the FITS file and shift the following HDUs forward. If `f` is the primary HDU in the file then it'll be replaced by a null primary HDU with no data and minimal header information.

Return a symbol to indicate the type of the new current HDU. Possible symbols are: `image_hdu`, `ascii_table`, or `binary_table`. The value of `hduNum` must range between 1 and the value returned by [`fits_get_num_hdus`](@ref).
