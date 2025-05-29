WeightingOp(weights::Vector{T}, rep::Int=1) where T

`weights`で入力ベクトルをインデックスごとに乗算する`LinearOperator`を生成します。

# 引数

  * `weights::Vector{T}` - 重みベクトル
  * `rep::Int=1`         - `weights`と乗算する必要があるサブ配列の数
