```
compress!(::Compressor, out_data, in_data)::Union{LibDeflateError, Int}
```

Use the passed `Compressor` to compress `in_data` into the first bytes of `out_data` using the DEFLATE algorithm. Data must fit in `out_data`.

Return the number of written bytes to the output, or a `LibDeflateError`.
