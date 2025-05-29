```
fits_read_imghdr(f::FITSFile, maxdim::Integer = 99)
```

Read the header of an image HDU, where `maxdim` represents the maximum number of dimensions to read. By default, `maxdim == 99` will read the size along every dimension of the image. The function returns the values of `SIMPLE::Bool`, `BITPIX::Int`, `NAXIS::Int`, `NAXES::Vector{Int}`, `PCOUNT::Int`, `GCOUNT::Int`, and `EXTEND::Bool`. The length of `NAXES` is set equal to `min(NAXIS, maxdim)`.

The `BITPIX` value indicates the data type of the image, and it may be converted to a Julia type using the [`type_from_bitpix`](@ref) function.

!!! note
    `PCOUNT` is typically `0` for image HDUs, and `GCOUNT` is typically `1` for modern files.

