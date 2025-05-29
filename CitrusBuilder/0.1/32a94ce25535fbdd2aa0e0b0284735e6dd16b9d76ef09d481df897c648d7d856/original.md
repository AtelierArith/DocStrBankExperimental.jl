```
same_default(component::AbstractSurveyComponent)
```

Return if the survey component uses the same default value for all languages.

# Examples

```julia-repl
julia> q = short_text_question("q1", "title", default="some default value")
julia> same_default(q)
false
```

```julia-repl
julia> q = short_text_question("q1", language_settings([
    language_setting("en", "title", default="some default value"),
    language_setting("de", "Titel")
], same_default=true))
julia> same_default(q)
true
```
