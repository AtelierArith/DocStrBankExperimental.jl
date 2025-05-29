```
unsafe_zlib_decompress!(
    size::Union{Base.SizeUnknown, Base.HasLength},
    ::Decompressor,
    out_ptr::Ptr, n_out::Integer,
    in_ptr::Ptr, len::Integer
)::Union{LibDeflateError, Int}
```

Zlibは、`in_ptr`から始まり`len`バイトのデータを`out_ptr`にデコンプレッションします。書き込まれたバイト数、または`LibDeflateError`を返します。`size`は`SizeUnknown`または`HasLength`である可能性があります。前者の場合、`n*out`は出力にどれだけのスペースがあるかを示します。後者の場合、`n*out`はペイロードがデコンプレッションされる正確なバイト数です。後者の方が速いです。

参照: [`zlib_decompress!`](@ref)
