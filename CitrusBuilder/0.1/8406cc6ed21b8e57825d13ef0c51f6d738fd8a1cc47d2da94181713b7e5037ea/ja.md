```
has_description(component::AbstractSurveyComponent, language::String)
```

指定された `language` に対して、調査コンポーネントに説明があるかどうかを返します。`language` が提供されていない場合は、コンポーネントのデフォルト言語の値が返されます。

# 例

```julia-repl
julia> q = short_text_question("q1", "title")
julia> has_description(q)
false

julia> q = short_text_question("q2", "title", description="some description")
julia> has_description(q)
true
```
