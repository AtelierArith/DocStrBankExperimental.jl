```
question_group(id, title::String; description, children)
```

単一言語の質問グループを構築します。`description` と `children` は省略可能なキーワード引数であり、省略することができます。

# 例

```julia-repl
julia> g = question_group(1, "a question group")
```

```julia-repl
julia> g = question_group(1, "a question group"; description="A simple description")
```

```julia-repl
julia> questions = [short_text_question("q$i", "question $i") for i in 1:3]
julia> g = question_group(1, "a question group"; children=questions)
```
