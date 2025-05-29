```
zlib_decompress!(
    ::Decompressor, output, input, [n_out::Integer]
)::Union{LibDeflateError, Int}
```

`input` から `output` へ zlib デコンプレッションを行います。デコンプレッションされたバイト数が正確に分かっている場合は、パフォーマンス向上のために `n_out` として渡してください。もし間違っている場合、関数はエラーを返します。

書き込まれたバイト数、または `LibDeflateError` を返します。

関連情報: [`unsafe_zlib_decompress!`](@ref)
