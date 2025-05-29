```
has_help(component::AbstractSurveyComponent, language::String)
```

Return whether or not the survey component has a `help` string for a given language. If `language` is not provided the value for the default language of the component is returned.

# Examples

```julia-repl
julia> q = short_text_question("q1", "title")
julia> has_help(q)
false

julia> q = short_text_question("q2", "title", help="some help")
julia> has_help(q)
true
```
