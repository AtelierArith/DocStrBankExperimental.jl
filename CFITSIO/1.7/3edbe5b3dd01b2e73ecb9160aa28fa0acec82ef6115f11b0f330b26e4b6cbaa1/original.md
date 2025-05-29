```
fits_read_subset(f::FITSFile,
                 fpixel::V, lpixel::V, inc::V,
                 [nulval],
                 data::StridedArray) where {V<:Union{Vector{<:Integer}, Tuple{Vararg{Integer}}}}
```

Read a rectangular section of the FITS image. The number of pixels to be read will be computed from the first and last pixels (specified as the `fpixel` and `lpixel` arguments respectively). The argument `inc` specifies the step-size in pixels along each dimension.

If the optional argument `nulval` is specified and is non-zero, null values in `data` will be replaced by it.

!!! note
    `data` needs to be stored contiguously in memory, and will be populated contiguously with the pixels that are read in.


See also: [`fits_read_pix`](@ref)
