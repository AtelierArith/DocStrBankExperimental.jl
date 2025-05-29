```
fits_write_pixnull(f::FITSFile, data::StridedArray, nulval)
```

Write the entire array `data` into the FITS file. The argument `nulval` specifies the values that are to be considered as "null values", and replaced by appropriate numbers corresponding to the element type of `data`.

!!! note
    `data` needs to be stored contiguously in memory.


See also: [`fits_write_pix`](@ref)
