```
zlib_compress!(
    ::Compressor, output, input
)::Union{LibDeflateError, Int}
```

`input`から`output`にZlib圧縮します。書き込まれたバイト数を返すか、`LibDeflateError`を返します。

関連情報: [`unsafe_zlib_compress!`](@ref)
