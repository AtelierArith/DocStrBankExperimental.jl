```
DataLoader(data::AbstractMatrix)
```

行列に基づいて[`DataLoader`](@ref)のインスタンスを作成します。

# 引数

詳細については[`DataLoader(::AbstractArray{<:Number, 3})`](@ref)を参照してください。

# 実装

内部的にデータはテンソルの形状`(size(data)..., 1)`に再形成され、一貫した表現が可能になります。
