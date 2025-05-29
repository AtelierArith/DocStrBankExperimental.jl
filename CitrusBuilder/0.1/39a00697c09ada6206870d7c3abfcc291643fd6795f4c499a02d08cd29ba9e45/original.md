```
date_select(id, language_settings::LanguageSettings; minimum=nothing, maximum=nothing, kwargs...)
date_select(id, title::String; help=nothing, kwargs...)
```

Construct a date select question.

# Keyword arguments

  * `minimum`: The minimum allowed date
  * `maximum`: The maximum allowed date

For a list of additional keyword arguments see [`Question`](@ref).
