```
fits_write_subset(f::FITSFile,
                  fpixel::V, lpixel::V,
                  data::StridedArray) where {V<:Union{Vector{<:Integer}, Tuple{Vararg{Integer}}}}
```

Write a rectangular section of the FITS image. The number of pixels to be written will be computed from the first and last pixels (specified as the `fpixel` and `lpixel` arguments respectively).

!!! note
    The section to be written out must be contiguous in memory, so all the dimensions aside from the last one must span the entire axis range. The arguments `fpixel` and `lpixel` must account for this.


See also: [`fits_write_pix`](@ref)
