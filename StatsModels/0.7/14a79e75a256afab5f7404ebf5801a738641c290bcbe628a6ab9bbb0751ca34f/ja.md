```
ModelMatrix(mf::ModelFrame)
```

`ModelFrame`をモデル化に適した数値行列に変換します

# フィールド

  * `m::AbstractMatrix{<:AbstractFloat}`: 生成された数値行列
  * `assign::Vector{Int}` 各列の`m`に対応する項のインデックス。

# コンストラクタ

```julia
ModelMatrix(mf::ModelFrame)
# 結果の行列の型を指定します（デフォルトはMatrix{Float64}）
ModelMatrix{T <: AbstractMatrix{<:AbstractFloat}}(mf::ModelFrame)
```
