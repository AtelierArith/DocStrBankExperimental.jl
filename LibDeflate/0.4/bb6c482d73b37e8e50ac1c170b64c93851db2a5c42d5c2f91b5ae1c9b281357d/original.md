```
unsafe_decompress!(
    s::IteratorSize, ::Decompressor,
    out_ptr::Ptr, n_out::Integer,
    in_ptr::Ptr, n_in::Integer
)::Union{Int, LibDeflateError}
```

Decompress `n_in` bytes from `in_ptr` to `out_ptr` using the DEFLATE algorithm, returning the number of decompressed bytes or the error encounted. `s` should be whether you know the decompressed size or not.

If `s` isa `Base.HasLength`, the number of decompressed bytes is given as `n_out`. This is more efficient, but will fail if the number is not correct.

If `s` isa `Base.SizeUnknown`, pass the size in bytes of the available space at the output to `n_out`.

See also: [`decompress!`](@ref)
