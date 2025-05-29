```
languages(component::AbstractSurveyComponent)
```

Return a vector of languages of a survey component.

# Examples

For components with a single language

```julia-repl
julia> s = survey(100000, "survey title")
julia> languages(s)
["en"]
```

For multi-language components

```julia-repl
julia> q = short_text_question("q1", language_settings([
    language_setting("en", "title"),
    language_setting("de", "Titel")
]))
julia> languages(q)
["en", "de"]
```
