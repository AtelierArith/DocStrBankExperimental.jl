```
question_group(id, language_settings::LanguageSettings; children)
```

Construct a multi-language question group. `children` is an optional keywird argument that can be omitted.

# Examples

```julia-repl
julia> g = question_group(1, language_settings([
    language_setting("de", "Eine Fragengruppe"),
    language_setting("en", "A question group")
]))
```
