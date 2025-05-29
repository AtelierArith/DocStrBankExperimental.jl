```
fits_get_img_type(f::FITSFile)
```

Return the datatype (bitpix) of the current image HDU. This may be converted to a Julia type by using the function [`type_from_bitpix`](@ref).
