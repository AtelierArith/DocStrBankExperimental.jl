```
eval_diff_tree_array(
    tree::AbstractExpressionNode{T},
    cX::AbstractMatrix{T},
    operators::OperatorEnum,
    direction::Integer;
    turbo::Union{Bool,Val}=Val(false)
) where {T<:Number}
```

式の前方導関数を計算します。これは、eval*tree*arrayと同様の構造と最適化を使用します。`direction`は、式内の特定の変数のインデックスです。例えば、`direction=1`は`x1`に関する導関数を示します。

# 引数

  * `tree::AbstractExpressionNode`: 評価する式ツリー。
  * `cX::AbstractMatrix{T}`: データ行列、形状は`[num_features, num_rows]`。
  * `operators::OperatorEnum`: `tree`を作成するために使用される演算子。
  * `direction::Integer`: 導関数を取る変数のインデックス。
  * `turbo::Union{Bool,Val}`: より高速な評価のためにLoopVectorization.jlを使用します。現在、これは特に効果はありません。

# 戻り値

  * `(evaluation, derivative, complete)::Tuple{AbstractVector{T}, AbstractVector{T}, Bool}`: 通常の評価、導関数、および評価が通常通り完了したか（またはnanまたはinfに遭遇したか）を示します。
