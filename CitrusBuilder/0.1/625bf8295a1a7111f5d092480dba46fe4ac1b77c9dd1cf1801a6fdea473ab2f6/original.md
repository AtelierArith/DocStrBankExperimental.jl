```
survey(id, title::String; children, settings)
```

Construct a single-language [`Survey`](@ref). `children` is an optional keyword argument and can be omitted.

# Examples

## Survey without children

```julia-repl
julia> s = survey(100000, "my survey")
Survey with 0 groups and 0 questions.
my survey (id: 100000)

```

## survey with children

```julia-repl
julia> s = survey(100000, "my survey", children = [
    question_group(1, "first question group"),
    question_group(2, "second question group")
])
Survey with 2 groups and 0 questions.
my survey (id: 100000)
├── first question group (id: 1)
└── second question group (id: 2)
```
