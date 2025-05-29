```
(ex::AbstractExpression)(X, operators::Union{AbstractOperatorEnum,Nothing}=nothing; kws...)
```

入力データ `X` に対して式 `ex` を評価します。

このメソッドは、式から演算子を展開し、`AbstractExpressionNode` に対する対応するメソッドを呼び出します。

# 引数

  * `X`: 式を評価するための入力データ。
  * `operators`: （オプション）使用する演算子。`nothing` の場合、演算子は式から取得されます。
  * `kws...`: 追加のキーワード引数。

# 戻り値

  * 入力データ `X` に対して式を評価した結果。
