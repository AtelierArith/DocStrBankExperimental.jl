```
fits_write_pix(f::FITSFile,
               fpixel::Union{Vector{<:Integer}, Tuple{Vararg{Integer}}},
               nelements::Integer, data::StridedArray)
```

Write `nelements` pixels from `data` into the FITS file starting from the pixel `fpixel`.

!!! note
    `data` needs to be stored contiguously in memory.


See also: [`fits_write_pixnull`](@ref)
