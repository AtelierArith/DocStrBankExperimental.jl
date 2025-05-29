```
string_tree(
    ex::AbstractExpression,
    operators::Union{AbstractOperatorEnum,Nothing}=nothing;
    variable_names=nothing,
    kws...
)
```

式を文字列表現に変換します。

このメソッドは、式から演算子と変数名を展開し、`AbstractExpressionNode`のために[`string_tree`](@ref StringsModule.string_tree)を呼び出します。

# 引数

  * `ex`: 文字列に変換する式。
  * `operators`: （オプション）使用する演算子。`nothing`の場合、演算子は式から取得されます。
  * `variable_names`: （オプション）文字列表現で使用する変数名。`nothing`の場合、変数名は式から取得されます。
  * `kws...`: 追加のキーワード引数。

# 戻り値

  * 式の文字列表現。
