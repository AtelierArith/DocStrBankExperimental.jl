```
survey(id, language_settings::LanguageSettings; children, settings)
```

Construct a multi-language [`Survey`](@ref). `children` is an optional keyword argument and can be omitted.

# Examples

## Survey without children

```julia-repl
julia> s = survey(100000, language_settings([
    language_setting("en", "A multi-language survey"),
    language_setting("de", "Eine mehrsprachige Umfrage")
]))
Survey with 0 groups and 0 questions.
A multi-language survey (id: 100000)
```

## Survey with children

```julia-repl
julia> s = survey(100000, language_settings([
    language_setting("en", "A multi-language survey"),
    language_setting("de", "Eine mehrsprachige Umfrage")
]), children = [question_group(1, language_settings([
    language_setting("en", "first question group"),
    language_setting("de", "Erste Fragengruppe")
]))])
Survey with 1 group and 0 questions.
A multi-language survey (id: 100000)
└── first question group (id: 1)
```
