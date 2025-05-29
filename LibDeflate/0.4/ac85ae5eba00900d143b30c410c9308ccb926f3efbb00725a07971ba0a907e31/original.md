```
unsafe_zlib_decompress!(
    size::Union{Base.SizeUnknown, Base.HasLength},
    ::Decompressor,
    out_ptr::Ptr, n_out::Integer,
    in_ptr::Ptr, len::Integer
)::Union{LibDeflateError, Int}
```

Zlib decompress data beginning at `in_ptr` and `len` bytes onwards, into `out_ptr`. Return the number of bytes written, or a `LibDeflateError`. `size``can be`SizeUnknown`or`HasLength`. If the former,`n*out`tells how much space is available at the output. If the latter,`n*out` is the exact number of bytes that the payload decompresses to. The latter is faster.

See also: [`zlib_decompress!`](@ref)
