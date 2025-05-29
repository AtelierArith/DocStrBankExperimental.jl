```
eval_grad_tree_array(tree::Union{AbstractExpression,AbstractExpressionNode}, X::AbstractArray, options::AbstractOptions; variable::Bool=false)
```

式の順方向微分を計算します。これは、eval*tree*arrayと同様の構造と最適化を使用します。`variable`は、特徴（すなわち`X`）に関して微分を取るべきか、または式内のすべての定数に関して微分を取るべきかを指定します。

# 引数

  * `tree::Union{AbstractExpression,AbstractExpressionNode}`: 評価する式ツリー。
  * `X::AbstractArray`: 各列がデータポイントであるデータ行列。
  * `options::AbstractOptions`: `tree`を作成するために使用される演算子を含むオプション。
  * `variable::Bool`: 特徴（すなわち`X` - `variable=true`）に関して微分を取るか、式内のすべての定数に関して微分を取るか（`variable=false`）。

# 戻り値

  * `(evaluation, gradient, complete)::Tuple{AbstractVector, AbstractArray, Bool}`: 通常の評価、勾配、および評価が通常通り完了したか（またはnanまたはinfに遭遇したか）を示します。
