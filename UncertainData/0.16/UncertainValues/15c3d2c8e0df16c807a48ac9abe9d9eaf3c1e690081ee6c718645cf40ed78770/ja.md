```
UncertainValue(empiricaldata::AbstractVector{T},
    d::Type{D}) where {D <: Distribution}
```

# 統計分布のコンストラクタ

データに対してタイプ `d` の分布をフィットさせ、それを経験的分布の表現として使用します。内部で `Distributions.fit` を呼び出します。

## 引数

  * **`empiricaldata`**: `distribution` をフィットさせるためのデータ。
  * **`distribution`**: `Distributions.jl` からの有効な単変量分布。
