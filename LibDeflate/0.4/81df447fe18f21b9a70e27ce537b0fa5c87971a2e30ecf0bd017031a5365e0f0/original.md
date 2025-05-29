```
decompress!(
    ::Decompressor, out_data, in_data, [n_out::Integer]
)::Union{LibDeflateError, Int}
```

Use the passed `Decompressor` to decompress the data at `in_data` into the first bytes of `out_data` using the DEFLATE algorithm, returning the number of written bytes to the output, or a `LibDeflateError`. Data must fit in `out_data`.

If the decompressed size is known beforehand, pass it as `n_out`. This will increase performance, but will fail if it is wrong.
