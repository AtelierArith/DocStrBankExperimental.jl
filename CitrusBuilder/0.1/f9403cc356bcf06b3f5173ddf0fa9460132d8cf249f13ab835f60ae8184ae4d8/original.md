```
question_group(children::Function, id, title::String; description)
```

Construct a single-language question group using `do...end` syntax. `description` is an optional keyword argument that can be omitted.

# Examples

```julia-repl
julia> g = question_group(1, "a question group") do
    short_text_question("q1", "first question")
end
```
