```
title(component::AbstractSurveyComponent, language::String)
```

Return the title of the a survey component for a given language. If `language` is not provided the title for the default language of the component is returned.

# Examples

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
