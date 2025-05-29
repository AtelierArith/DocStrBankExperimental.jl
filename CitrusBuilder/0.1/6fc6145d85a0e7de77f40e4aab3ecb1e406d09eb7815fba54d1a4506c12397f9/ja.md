```
has_default(component::AbstractSurveyComponent, language::String)
```

指定された言語に対して、調査コンポーネントがデフォルト値を持っているかどうかを返します。`language`が提供されていない場合は、コンポーネントのデフォルト言語のデフォルト値が返されます。

# 例

```julia-repl
julia> q = short_text_question("q1", "title")
julia> has_default(q)
false
```

```julia-repl
julia> q = short_text_question("q2", "title", default="placeholder")
julia> has_default(q)
true
```
