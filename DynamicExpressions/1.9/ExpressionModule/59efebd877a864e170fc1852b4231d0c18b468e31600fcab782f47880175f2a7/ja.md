```
eval_grad_tree_array(
    ex::AbstractExpression,
    cX::AbstractMatrix,
    operators::Union{AbstractOperatorEnum,Nothing}=nothing;
    kws...
)
```

式の順方向微分を計算します。

このメソッドは式から演算子を展開し、`AbstractExpressionNode`のために[`eval_grad_tree_array`](@ref EvaluateDerivativeModule.eval_grad_tree_array)を呼び出します。

# 引数

  * `ex`: 評価する式。
  * `cX`: データ行列。
  * `operators`: （オプション）使用する演算子。`nothing`の場合、演算子は式から取得されます。
  * `kws...`: 追加のキーワード引数。

# 戻り値

  * 結果、勾配、および評価の成功を示すタプル `(output, gradient, complete)`。
