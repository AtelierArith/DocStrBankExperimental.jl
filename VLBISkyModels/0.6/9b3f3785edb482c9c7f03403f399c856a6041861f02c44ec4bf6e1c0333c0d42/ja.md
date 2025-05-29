```julia
struct ZeroModel{T} <: ComradeBase.AbstractModel
```

すべてに対してゼロを返す`empty`なモデルを定義します。

# 注意事項

これは`FillArrays`を使用して0を返すため、すべてが非アロケーションである必要があります。
