```
write_avif(dest_file::AbstractString, image::AbstractMatrix{<:Colorant}; kwargs...) -> Integer
write_avif(dest_file::AbstractString, image_arr::TVector; kwargs...) -> Integer
```

Utility function that encodes a matrix of `Colorant` or an array of matrices of `Colorant` into a `dest_file` Avif image.
