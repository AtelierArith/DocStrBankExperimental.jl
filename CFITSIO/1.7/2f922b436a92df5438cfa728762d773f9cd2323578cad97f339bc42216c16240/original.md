```
fits_insert_img(f::FITSFile, T::Type,
                naxes::Union{Vector{<:Integer}, Tuple{Vararg{Integer}}}; prepend_primary::Bool = false)
```

Insert a new image extension immediately following the current HDU (CHDU), or insert a new primary array at the beginning of the file.

A new primary array may be inserted at the beginning of the FITS file by calling `fits_insert_img` with `prepend_primary` set to `true`. In this case, the existing primary HDU is converted to an image extension, and the new primary array will become the CHDU.

The inserted array has an eltype `T` and size `naxes`.

```
fits_insert_img(f::FITSFile, a::AbstractArray{<:Real}; prepend_primary::Bool = false)
```

Insert a new image HDU with an element type of `eltype(a)` and a size of `size(a)` that is capable of storing the array `a`. The flag `prepend_primary` may be specified to insert a new primary array at the beginning of the FITS file.
