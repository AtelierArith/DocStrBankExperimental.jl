```
unsafe_decompress!(
    s::IteratorSize, ::Decompressor,
    out_ptr::Ptr, n_out::Integer,
    in_ptr::Ptr, n_in::Integer
)::Union{Int, LibDeflateError}
```

DEFLATEアルゴリズムを使用して、`in_ptr`から`out_ptr`に`n_in`バイトをデコンプレッションし、デコンプレッションされたバイト数または発生したエラーを返します。`s`は、デコンプレッションされたサイズを知っているかどうかを示す必要があります。

`s`が`Base.HasLength`の場合、デコンプレッションされたバイト数は`n_out`として与えられます。これはより効率的ですが、数が正しくない場合は失敗します。

`s`が`Base.SizeUnknown`の場合、出力の利用可能なスペースのバイト数を`n_out`に渡します。

参照: [`decompress!`](@ref)
