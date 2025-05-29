```
has_description(component::AbstractSurveyComponent, language::String)
```

Returns whether or not the survey component has a description for a given `language`. If `language` is not provided the value for the default language of the component is returned.

# Examples

```julia-repl
julia> q = short_text_question("q1", "title")
julia> has_description(q)
false

julia> q = short_text_question("q2", "title", description="some description")
julia> has_description(q)
true
```
