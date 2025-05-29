```
question_group(id, title::String; description, children)
```

Construct a single-language question group. Both `description` and `children` are optional keyword arguments that can be omitted.

# Examples

```julia-repl
julia> g = question_group(1, "a question group")
```

```julia-repl
julia> g = question_group(1, "a question group"; description="A simple description")
```

```julia-repl
julia> questions = [short_text_question("q$i", "question $i") for i in 1:3]
julia> g = question_group(1, "a question group"; children=questions)
```
