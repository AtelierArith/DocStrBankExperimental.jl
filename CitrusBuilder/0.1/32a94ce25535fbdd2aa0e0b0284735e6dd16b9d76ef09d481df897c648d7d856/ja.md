```
same_default(component::AbstractSurveyComponent)
```

すべての言語で同じデフォルト値を使用しているかどうかを返します。

# 例

```julia-repl
julia> q = short_text_question("q1", "title", default="some default value")
julia> same_default(q)
false
```

```julia-repl
julia> q = short_text_question("q1", language_settings([
    language_setting("en", "title", default="some default value"),
    language_setting("de", "Titel")
], same_default=true))
julia> same_default(q)
true
```
