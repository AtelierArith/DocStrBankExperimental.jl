```
DataLoader(data::AbstractVector)
```

ベクトルに基づいて `DataLoader` のインスタンスを作成します。

# 拡張ヘルプ

`DataLoader` への入力がベクトルである場合、このベクトルは一次元の時系列データを表すと見なされ、次のように処理されます：

```julia
    DataLoader(data::AbstractVector; autoencoder=true) = DataLoader(reshape(data, 1, length(data)); autoencoder = autoencoder)
```
