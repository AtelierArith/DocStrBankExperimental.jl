```
numerical_input(id, language_settings::LanguageSettings; minimum=nothing, maximum=nothing, integer_only=false, kwargs...)
numerical_input(id, title::String; help=nothing, kwargs...)
```

Construct a multi-language numerical input.

# Keyword arguments

  * `minimum`: The minimum value
  * `maximum`: The maximum value
  * `integer_only`: Permit only integer values
