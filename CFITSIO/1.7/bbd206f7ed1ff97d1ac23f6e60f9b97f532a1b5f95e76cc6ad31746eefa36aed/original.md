```
fits_resize_img(f::FITSFile, sz::Union{Vector{<:Integer}, Tuple{Vararg{Integer}}})
```

Resize the image to the new size `sz`. The element type is preserved, and the number of dimensions is set equal to `length(sz)`.
