```
add_language!(
    highlighter::Highlighter,
    language::Language;
    scope::String,
    highlights_query::Union{Nothing,String}=nothing,
    injections_query::Union{Nothing,String}=nothing,
    locals_query::Union{Nothing,String} = nothing,
    injection_regex::String = string("^", language.name),
)
```

Adds a language definition to the given highlighter.
