```
FITS_pointer
```

Object holding an array of [`HDU_ptr`](@ref) objects.

The fields are:

  * `.nblock`     : block count (`::Int`)
  * `.nhdu`       : hdu count (`::Int`)
  * `.block_start`: start-of-block pointers: (`::Tuple(Vector{Int})`)
  * `.block_stop`: end-of-block pointers: (`::Tuple(Vector{Int})`)
  * `.hdu_start`: start-of-hdu pointers: (`::Tuple(Vector{Int})`)
  * `.hdu_stop`: end-of-hdu pointers: (`::Tuple(Vector{Int})`)
  * `.hdr_start`: start-of-header pointers: (`::Tuple(Vector{Int})`)
  * `.hdr_stop`: end-of-header pointers: (`::Tuple(Vector{Int}))`)
  * `.data_start`: start-of-data pointers: (`::Tuple(Vector{Int})`)
  * `.data_stop`: end-of-data pointers: (`::Tuple(Vector{Int})`)
