```
(tree::AbstractExpressionNode)(X, operators::GenericOperatorEnum; kws...)
```

# 引数

  * `X::AbstractArray`: ツリーを評価するための入力データ。
  * `operators::GenericOperatorEnum`: ツリーで使用される演算子。
  * `kws...`: `eval_tree_array` に渡される。

# 戻り値

  * `output`: 評価の結果。評価が失敗した場合、最初の引数には `nothing` が返される。完全な `false` は、演算子が定義されていない入力タイプに対して呼び出されたことを意味する。この動作は `throw_errors=false` を設定することで変更できる。
