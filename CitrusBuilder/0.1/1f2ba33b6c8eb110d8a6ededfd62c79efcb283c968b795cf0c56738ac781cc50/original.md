```
default(component::AbstractSurveyComponent, language::String)
```

Return the default value of a survey component. If `language` is provided the default value for the default language of the component is returned.

# Examples

```julia-repl
julia> q = short_text_question("q1", language_settings([
    language_setting("en", "title", default="placeholder"),
    language_setting("de", "Titel", default="Platzhalter")
]))
julia> default(q)
"placeholder"
julia> default(q, "en")
"placeholder"
julia> default(q, "de")
"Platzhalter"
```
