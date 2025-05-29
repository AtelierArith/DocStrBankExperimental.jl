```
fits_read_pix(f::FITSFile, data::StridedArray, [nulval])
```

Read `length(data)` pixels from the FITS file into `data` starting from the first pixel. The optional argument `nulval`, if specified and non-zero, is used to replace any null value present in the array.

!!! note
    `data` needs to be stored contiguously in memory.


See also: [`fits_read_pixnull`](@ref)
