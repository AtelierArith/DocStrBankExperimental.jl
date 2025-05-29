```
short_text_question(id, language_settings::LanguageSettings; kwargs...)
short_text_question(id, title::String; help=nothing, default=nothing, kwargs...)
```

Construct a short text question. If the question is constructed using a `title`, the global default language is used by default.

For a list of available keyword arguments see [`Question`](@ref).

# Examples

Simple short text questions using a single language can be constructed using a `title` string.

```julia-repl
julia> q = short_text_question("q1", "my question")
```

To construct a multi-language short text question, use [`language_settings`](@ref).

```julia-repl
julia> q = short_text_question("q2", language_settings([
    language_setting("en", "question title"),
    language_setting("de", "Fragetitel")
]))
```
