```
string_tree(tree::AbstractExpressionNode, options::AbstractOptions; kws...)
```

方程式を文字列に変換します。

# 引数

  * `tree::AbstractExpressionNode`: 文字列に変換する方程式。
  * `options::AbstractOptions`: 演算子の定義を保持するオプション。
  * `variable_names::Union{Array{String, 1}, Nothing}=nothing`: 各特徴のために印刷する変数。
