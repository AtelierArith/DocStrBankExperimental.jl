```
languages(component::AbstractSurveyComponent)
```

調査コンポーネントの言語のベクトルを返します。

# 例

単一言語のコンポーネントの場合

```julia-repl
julia> s = survey(100000, "survey title")
julia> languages(s)
["en"]
```

多言語コンポーネントの場合

```julia-repl
julia> q = short_text_question("q1", language_settings([
    language_setting("en", "title"),
    language_setting("de", "Titel")
]))
julia> languages(q)
["en", "de"]
```
