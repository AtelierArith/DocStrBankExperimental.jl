```
fits_read_pixnull(f::FITSFile,
                  fpixel::Union{Vector{<:Integer}, Tuple{Vararg{Integer}}},
                  nelements::Integer, data::StridedArray, nullarray::Array{UInt8})
```

Read `nelements` pixels from the FITS file into `data` starting from the pixel `fpixel`. At output, the indices of `nullarray` where `data` has a corresponding null value are set to `1`.

!!! note
    `data` needs to be stored contiguously in memory.


See also: [`fits_read_pix`](@ref)
