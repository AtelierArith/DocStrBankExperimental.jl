```
survey(children::Function, id, language_settings::LanguageSettings; settings)
```

`do ... end` 構文を使用して多言語 [`Survey`](@ref) を構築します。

# 例

```julia-repl
julia> s = survey(100000, language_settings([
    language_setting("en", "A multi-language survey"),
    language_setting("de", "Eine mehrsprachige Umfrage")
])) do
    question_group(1, language_settings([
        language_setting("en", "first question group"),
        language_setting("de", "Erste Fragengruppe")
    ]))
end
Survey with 1 group and 0 questions.
A multi-language survey (id: 100000)
└── first question group (id: 1)

```
