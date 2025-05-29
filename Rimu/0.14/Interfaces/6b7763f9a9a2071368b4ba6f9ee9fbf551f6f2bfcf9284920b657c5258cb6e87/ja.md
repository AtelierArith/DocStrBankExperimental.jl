```
compress!([::CompressionStrategy,] v) -> ::NTuple{N,::Symbol}, ::NTuple{N}
compress!([::CompressionStrategy,] w, v) -> ::NTuple{N,::Symbol}, ::NTuple{N}
```

ベクトル `v` を圧縮します。1引数バージョンはベクトルをインプレースで圧縮します。2引数バージョンは結果を `w` に格納します。`v` の [`StochasticStyle`](@ref) に関連付けられた [`CompressionStrategy`](@ref) が圧縮のタイプを決定するために使用されます。

報告される統計の名前と値を含む2つのタプルを返します。
