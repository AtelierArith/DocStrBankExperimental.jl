```
fdm_operator_matrix(op::AbstractFiniteDifferenceOperator{TR}; boundary::Bool=false, transpose::Bool=false) -> BandedMatrix{TR}
```

有限差分演算子のバンド行列表現を作成します。

# 引数

  * `op::AbstractFiniteDifferenceOperator{TR}`: 有限差分演算子
  * `boundary::Bool=true`: 境界重みを含めるかどうか
  * `transpose::Bool=false`: 行列を転置するかどうか
