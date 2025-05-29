```
default_language(component::AbstractSurveyComponent)
```

Return the default language of a survey component. The default language is defined as the first language of the component.

# Examples

```julia-repl
julia> g = question_group(1, "group title")
julia> default_language(g)
"en"
```

!!! note
    The default language of a survey component is not necessarily equal to the global default language set by [`set_default_language!`](@ref).


```julia-repl
julia> default_language()
"en"
julia> g = question_group(1, language_settings([
    language_setting("de", "Gruppentitel"),
    language_settings("en", "group title")
]))
julia> default_language(g)
"de"
```
