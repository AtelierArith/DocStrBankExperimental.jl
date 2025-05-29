```
survey(children::Function, id, title::String; settings)
```

Construct a single-language [`Survey`](@ref) using `do ... end` syntax.

# Examples

```julia-repl
julia> s = survey(100000, "my survey") do
    question_group(1, "first question group"),
    question_group(2, "second question group")
end
Survey with 2 groups and 0 questions.
my survey (id: 100000)
├── first question group (id: 1)
└── second question group (id: 2)

```
