```
WeightingOp(::Type{T}; weights::Vector{T}, rep::Int=1) where T
```

は、入力ベクトルをインデックスごとに `weights` で乗算する `LinearOperator` を生成します。

# 引数

  * `weights::Vector{T}` - 重みベクトル
  * `rep::Int=1`         - `weights` と乗算する必要があるサブ配列の数
