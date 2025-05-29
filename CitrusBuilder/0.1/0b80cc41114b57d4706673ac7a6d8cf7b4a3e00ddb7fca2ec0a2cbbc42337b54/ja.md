```
title(component::AbstractSurveyComponent, language::String)
```

与えられた言語の調査コンポーネントのタイトルを返します。`language`が提供されていない場合は、コンポーネントのデフォルト言語のタイトルが返されます。

# 例

```julia-repl
julia> g = question_group(1, "my title")
julia> title(g)
"my title"
```

```julia-repl
julia> g = question_group(1, language_settings([
    language_setting("en", "my title"),
    language_setting("de", "Mein Titel")
]))
julia> title(g, "en")
"my title"
julia> title(g, "de")
"Mein Titel"
```
