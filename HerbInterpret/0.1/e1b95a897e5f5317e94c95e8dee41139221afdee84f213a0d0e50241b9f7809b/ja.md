```
execute_on_input(grammar::AbstractGrammar, program::RuleNode, input::Dict{Symbol, T})::Any where T
```

与えられた `grammar` を使用して `RuleNode` プログラムを式に変換し、その後、`grammar` から導出されたシンボルテーブルと単一の入力辞書 `input` を使用してこの式を評価します。

# 引数

  * `grammar::AbstractGrammar`: `RuleNode` を実行可能な式に変換するために使用される文法オブジェクト。
  * `program::RuleNode`: 変換および評価される `RuleNode` として表現されたプログラム。
  * `input::Dict{Symbol, T}`: 生成された式で使用されるシンボルの入力値を提供する辞書。

# 戻り値

  * `Any`: 与えられた入力辞書を使用して生成された式を評価した結果。
