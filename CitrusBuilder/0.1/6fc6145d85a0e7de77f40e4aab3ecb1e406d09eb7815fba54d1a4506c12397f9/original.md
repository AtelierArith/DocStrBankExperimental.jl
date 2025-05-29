```
has_default(component::AbstractSurveyComponent, language::String)
```

Return whether or not a survey component has a default value for a given language. If `language` is not provided the default value for the default language of the component is returned.

# Examples

```julia-repl
julia> q = short_text_question("q1", "title")
julia> has_default(q)
false
```

```julia-repl
julia> q = short_text_question("q2", "title", default="placeholder")
julia> has_default(q)
true
```
