```
has_help(component::AbstractSurveyComponent, language::String)
```

与えられた言語のために、調査コンポーネントが `help` 文字列を持っているかどうかを返します。`language` が提供されていない場合は、コンポーネントのデフォルト言語の値が返されます。

# 例

```julia-repl
julia> q = short_text_question("q1", "title")
julia> has_help(q)
false

julia> q = short_text_question("q2", "title", help="some help")
julia> has_help(q)
true
```
