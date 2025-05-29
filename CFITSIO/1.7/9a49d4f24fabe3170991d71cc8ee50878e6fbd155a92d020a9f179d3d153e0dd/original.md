```
fits_write_pixnull(f::FITSFile,
                   fpixel::Union{Vector{<:Integer}, Tuple{Vararg{Integer}}},
                   nelements::Integer, data::StridedArray, nulval)
```

Write `nelements` pixels from `data` into the FITS file starting from the pixel `fpixel`. The argument `nulval` specifies the values that are to be considered as "null values", and replaced by appropriate numbers corresponding to the element type of `data`.

!!! note
    `data` needs to be stored contiguously in memory.


See also: [`fits_write_pix`](@ref)
