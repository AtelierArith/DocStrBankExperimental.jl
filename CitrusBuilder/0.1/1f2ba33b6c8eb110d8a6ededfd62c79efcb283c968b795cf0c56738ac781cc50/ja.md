```
default(component::AbstractSurveyComponent, language::String)
```

サーベイコンポーネントのデフォルト値を返します。`language`が提供されると、コンポーネントのデフォルト言語のデフォルト値が返されます。

# 例

```julia-repl
julia> q = short_text_question("q1", language_settings([
    language_setting("en", "title", default="placeholder"),
    language_setting("de", "Titel", default="Platzhalter")
]))
julia> default(q)
"placeholder"
julia> default(q, "en")
"placeholder"
julia> default(q, "de")
"Platzhalter"
```
