```
eval_diff_tree_array(tree::Union{AbstractExpression,AbstractExpressionNode}, X::AbstractArray, options::AbstractOptions, direction::Int)
```

式の前方導関数を計算します。これは、eval*tree*arrayと同様の構造と最適化を使用します。`direction`は、式内の特定の変数のインデックスです。例えば、`direction=1`は`x1`に関する導関数を示します。

# 引数

  * `tree::Union{AbstractExpression,AbstractExpressionNode}`: 評価する式ツリー。
  * `X::AbstractArray`: 各列がデータポイントであるデータ行列。
  * `options::AbstractOptions`: `tree`を作成するために使用される演算子を含むオプション。
  * `direction::Int`: 導関数を取る変数のインデックス。

# 戻り値

  * `(evaluation, derivative, complete)::Tuple{AbstractVector, AbstractVector, Bool}`: 通常の評価、導関数、および評価が通常通り完了したか（またはnanまたはinfに遭遇したか）を示すブール値。
