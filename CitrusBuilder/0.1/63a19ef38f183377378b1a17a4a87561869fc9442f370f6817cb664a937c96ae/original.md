```
question_group(children::Function, id, language_settings::LanguageSettings)
```

Construct a multi-language question group using `do...end` syntax.

# Examples

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
