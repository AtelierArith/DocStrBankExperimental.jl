```
description(component::AbstractSurveyComponent, language::String)
```

指定された言語の調査コンポーネントの説明を返します。`language`が提供されていない場合は、コンポーネントのデフォルト言語の説明が返されます。

# 例

```julia-repl
julia> q = short_text_question("q1", "title", description="この質問に答えてください")
julia> description(q)
"この質問に答えてください"

julia> q = short_text_question("q2", language_settings([
    language_setting("en", "いくつかの説明"),
    language_setting("de", "Eine Beschreibung")
]))
julia> description(q)
"いくつかの説明"

julia> description(q, "de")
"Eine Beschreibung"
```
