```
fits_write_pix(f::FITSFile, data::StridedArray)
```

Write the entire array `data` into the FITS file.

!!! note
    `data` needs to be stored contiguously in memory.


See also: [`fits_write_pixnull`](@ref), [`fits_write_subset`](@ref)
