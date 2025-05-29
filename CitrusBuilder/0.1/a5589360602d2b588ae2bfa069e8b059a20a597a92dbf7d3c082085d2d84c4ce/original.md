```
survey(children::Function, id, language_settings::LanguageSettings; settings)
```

Construct a multi-language [`Survey`](@ref) using `do ... end` syntax.

# Examples

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
