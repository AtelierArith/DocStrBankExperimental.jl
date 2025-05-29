```
DataLoader(dl, backend)
```

既存の `DataLoader` のインスタンスに基づいて新しい `backend` の `DataLoader` の新しいインスタンスを作成します。

これは、元の `dl` に使用されるのと同じサイズの新しいメモリを割り当て、その後データをコピーします。

デフォルトでは、データ型は変更されず、すなわち `eltype(DataLoader(dl, backend)) == eltype(dl)` は `true` です。

データ型を変更したい場合は、例えば次のように書きます。

```julia
    DataLoader(dl, backend, Float32)
```

# 引数

オプションのキーワード引数があります。

  * `autoencoder = nothing`。

デフォルトでは、これは `dl` からオートエンコーダーのプロパティを継承します。

[`DataLoader(data::AbstractArray{<:Number, 3})`](@ref) のドキュメントを参照してください。
