```
unsafe_compress!(
    ::Compressor, out_ptr::Ptr, n_out::Integer, in_ptr::Ptr, n_in::Integer
)::Union{Int. LibDeflateError}
```

Use the passed `Compressor` to compress `n_in` bytes from the pointer `in_ptr` to the pointer `n_out` where there are `n_out` bytes of space to write to.

Return the number of written bytes to the output, or a `LibDeflateError`.

See also: [`compress!`](@ref)
