SensitivityOp(sensMaps::AbstractMatrix{T}, numContr=1)

指定された`sensMaps`のコイル感度を用いて、与えられた画像との乗算を行う`LinearOperator`を構築します。

# 引数

  * `sensMaps`    - 感度マップ (1. 次元 -> ボクセル, 2. 次元 -> コイル)
  * `numEchoes`   - 演算子が適用されるコントラストの数
