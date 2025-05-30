```
type_compress!(df, compress_float = false, verbose = false)
```

DataFrameをより小さいビットの型を使用して圧縮します。安全であれば、`Int*`および`UInt*`をダウングレードします。`CategoricalVector`は`DataFrames.compress`を使用して圧縮されます。

`Vector{String}`の場合、ユニークな値の数が2^16未満であれば、`CategoricalVector`に変換され、それ以外の場合は`WeakRefStrings.StringVector`として保存されます。

`compress_float = true`の場合、`Float64`は`Float32`にダウングレードされますが、これは計算が精度を減らして行われることを意味するため注意が必要です。
