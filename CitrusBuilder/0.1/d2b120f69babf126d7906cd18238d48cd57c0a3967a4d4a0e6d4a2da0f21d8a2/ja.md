```
id(component::AbstractSurveyComponent)
```

調査コンポーネントの `id` を返します。

# 例

```julia-repl
julia> q = short_text_question("q1", "title")
julia> id(q)
"q1"
```
