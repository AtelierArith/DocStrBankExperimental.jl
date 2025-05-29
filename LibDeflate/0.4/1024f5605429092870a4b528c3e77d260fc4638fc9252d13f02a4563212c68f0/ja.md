```
unsafe_zlib_compress!(
    ::Compressor,
    out_ptr::Ptr, max_outlen::Integer,
    in_ptr::Ptr, len::Integer
)::Union{LibDeflateError, Int}
```

`in_ptr`から始まり`len`バイト分のデータを`out_ptr`に圧縮します。書き込まれたバイト数、または`LibDeflateError`を返します。

関連情報: [`zlib_compress!`](@ref)
