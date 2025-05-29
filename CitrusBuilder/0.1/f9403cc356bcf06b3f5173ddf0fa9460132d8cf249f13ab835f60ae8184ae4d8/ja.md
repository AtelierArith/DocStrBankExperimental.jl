```
question_group(children::Function, id, title::String; description)
```

`do...end`構文を使用して単一言語の質問グループを構築します。`description`は省略可能なキーワード引数です。

# 例

```julia-repl
julia> g = question_group(1, "質問グループ") do
    short_text_question("q1", "最初の質問")
end
```
