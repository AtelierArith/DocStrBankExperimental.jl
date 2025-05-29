```
help(component::AbstractSurveyComponent, language::String)
```

Return the help string of a survey component for a given language. If `language` is not provided the help for the default language of the component is returned.

# Examples

```julia-repl
julia> q = short_text_question("q1", "my question", help="some help")
julia> help(q)
"some help"
```
