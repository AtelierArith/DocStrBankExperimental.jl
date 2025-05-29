```
eval_grad_tree_array(tree::AbstractExpressionNode{T}, cX::AbstractMatrix{T}, operators::OperatorEnum; variable::Union{Bool,Val}=Val(false), turbo::Union{Bool,Val}=Val(false))
```

式の順方向微分を計算します。`eval*tree*array`と同様の構造と最適化を使用します。`variable`は、特徴（すなわち、cX）に関して微分を取るべきか、または式内のすべての定数に関して微分を取るべきかを指定します。

# 引数

  * `tree::AbstractExpressionNode{T}`: 評価する式ツリー。
  * `cX::AbstractMatrix{T}`: 各列がデータポイントであるデータ行列。
  * `operators::OperatorEnum`: `tree`を作成するために使用される演算子。
  * `variable::Union{Bool,Val}`: 特徴（すなわち、`cX` - `variable=true`）に関して微分を取るか、式内のすべての定数に関して微分を取るか（`variable=false`）。
  * `turbo::Union{Bool,Val}`: より高速な評価のためにLoopVectorization.jlを使用します。現在、これには効果がありません。

# 戻り値

  * `(evaluation, gradient, complete)::Tuple{AbstractVector{T}, AbstractMatrix{T}, Bool}`: 通常の評価、勾配、および評価が通常通り完了したか（またはnanまたはinfに遭遇したか）を示します。
