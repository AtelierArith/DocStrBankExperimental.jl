```
fits_read_pix(f::FITSFile,
              fpixel::NTuple{Vector{<:Integer}, Tuple{Vararg{Integer}}},
              nelements::Integer, [nulval], data::StridedArray)
```

Read `nelements` pixels from the FITS file into `data` starting from the pixel `fpixel`. If the optional argument `nulval` is specified and is non-zero, any null value present in the array will be replaced by it.

!!! note
    `data` needs to be stored contiguously in memory.


See also: [`fits_read_pixnull`](@ref), [`fits_read_subset`](@ref)
