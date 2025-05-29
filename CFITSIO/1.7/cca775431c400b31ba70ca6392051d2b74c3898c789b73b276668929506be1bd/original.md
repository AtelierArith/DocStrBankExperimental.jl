```
fits_read_pixnull(f::FITSFile, data::StridedArray, nullarray::Array{UInt8})
```

Read `length(data)` pixels from the FITS file into `data` starting from the first pixel. At output, the indices of `nullarray` where `data` has a corresponding null value are set to `1`.

!!! note
    `data` needs to be stored contiguously in memory.


See also: [`fits_read_pix`](@ref)
