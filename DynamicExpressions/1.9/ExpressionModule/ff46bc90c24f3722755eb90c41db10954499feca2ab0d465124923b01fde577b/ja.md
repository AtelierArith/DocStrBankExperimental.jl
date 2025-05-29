```
eval_tree_array(
    ex::AbstractExpression,
    cX::AbstractMatrix,
    operators::Union{AbstractOperatorEnum,Nothing}=nothing;
    kws...
)
```

与えられた入力データ行列に対して式を評価します。

このメソッドは、式から演算子を展開し、`AbstractExpressionNode`のために[`eval_tree_array`](@ref EvaluateModule.eval_tree_array)を呼び出します。

# 引数

  * `ex`: 評価する式。
  * `cX`: 入力データ行列。
  * `operators`: （オプション）使用する演算子。`nothing`の場合、演算子は式から取得されます。
  * `kws...`: 追加のキーワード引数。

# 戻り値

  * 結果と評価の成功を示すタプル`(output, complete)`。
