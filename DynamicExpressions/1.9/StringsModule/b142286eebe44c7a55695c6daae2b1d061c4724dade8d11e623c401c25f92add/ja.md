```
string_tree(
    tree::AbstractExpressionNode{T},
    operators::Union{AbstractOperatorEnum,Nothing}=nothing;
    f_variable::F1=string_variable,
    f_constant::F2=string_constant,
    variable_names::Union{Array{String,1},Nothing}=nothing,
    # Deprecated
    varMap=nothing,
)::String where {T,F1<:Function,F2<:Function}
```

方程式を文字列に変換します。

# 引数

  * `tree`: 文字列に変換する木
  * `operators`: 木を定義するために使用される演算子

# キーワード引数

  * `f_variable`: (オプション) 変数を文字列に変換する関数で、引数は `(feature::UInt8, variable_names)` です。
  * `f_constant`: (オプション) 定数を文字列に変換する関数で、引数は `(val,)` です。
  * `variable_names::Union{Array{String, 1}, Nothing}=nothing`: (オプション) 各特徴に対して印刷する変数。
