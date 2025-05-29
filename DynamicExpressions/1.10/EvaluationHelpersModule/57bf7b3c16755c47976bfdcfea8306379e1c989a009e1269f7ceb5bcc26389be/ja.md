```
(tree::AbstractExpressionNode)(X, operators::OperatorEnum; kws...)
```

与えられた入力データ行列に対して二項木（方程式）を評価します。オペレーターには使用されるすべてのオペレーターが含まれています。この関数は、メモリ使用量を減らすためにダブレットとトリプレットの操作を融合します。

# 引数

  * `tree::AbstractExpressionNode`: 評価する木のルートノード。
  * `X::AbstractMatrix{T}`: 木を評価するための入力データで、形状は `[num_features, num_rows]` です。
  * `operators::OperatorEnum`: 木で使用されるオペレーター。
  * `kws...`: `eval_tree_array` に渡されます。

# 戻り値

  * `output::AbstractVector{T}`: 結果で、1D 配列です。評価中に NaN、Inf、またはその他の失敗が発生した場合、出力配列全体が NaN に設定されます。
