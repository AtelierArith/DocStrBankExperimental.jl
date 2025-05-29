```
unsafe_compress!(
    ::Compressor, out_ptr::Ptr, n_out::Integer, in_ptr::Ptr, n_in::Integer
)::Union{Int. LibDeflateError}
```

渡された `Compressor` を使用して、ポインタ `in_ptr` から `n_in` バイトを圧縮し、書き込むためのスペースが `n_out` バイトあるポインタ `n_out` に書き込みます。

出力に書き込まれたバイト数、または `LibDeflateError` を返します。

参照: [`compress!`](@ref)
