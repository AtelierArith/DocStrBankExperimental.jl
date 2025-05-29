```
execute_on_input(grammar::AbstractGrammar, program::RuleNode, input::Vector{T})::Vector{Any} where T <: Dict{Symbol, <:Any}
```

`RuleNode` プログラムを与えられた `grammar` を使用して式に変換し、その後、ベクター `input` 内の各入力辞書に対してこの式を評価し、`grammar` から導出されたシンボルテーブルを使用して `execute_on_input(tab::SymbolTable, expr::Any, input::Dict{Symbol, T})` を実行します。

# 引数

  * `grammar::AbstractGrammar`: `RuleNode` を実行可能な式に変換するために使用される文法オブジェクト。
  * `program::RuleNode`: 変換および評価される `RuleNode` として表現されたプログラム。
  * `input::Vector{T}`: 生成された式で使用されるシンボルの入力値を提供する辞書のベクター。

# 戻り値

  * `Vector{Any}`: 各入力辞書に対して生成された式を評価した結果を含むベクター。
