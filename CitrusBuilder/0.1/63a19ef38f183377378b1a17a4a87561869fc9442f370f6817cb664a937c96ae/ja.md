```
question_group(children::Function, id, language_settings::LanguageSettings)
```

`do...end` 構文を使用して多言語の質問グループを構築します。

# 例

```julia-repl
julia> g = question_group(1, language_settings([
    language_setting("de", "Eine Fragengruppe"),
    language_setting("en", "A question group")
])) do
    short_text_question("q1", language_settings([
        language_setting("de", "Eine Frage")
        language_setting("en", "A question")
    ]))
end
```
