```
description(component::AbstractSurveyComponent, language::String)
```

Returns the description of a survey component for a given language. If `language` is not provided the description for the default language of the component is returned.

# Examples

```julia-repl
julia> q = short_text_question("q1", "title", description="answer this question")
julia> description(q)
"answer this question"

julia> q = short_text_question("q2", language_settings([
    language_setting("en", "some description"),
    language_setting("de", "Eine Beschreibung")
]))
julia> description(q)
"some description"

julia> description(q, "de")
"Eine Beschreibung"
```
