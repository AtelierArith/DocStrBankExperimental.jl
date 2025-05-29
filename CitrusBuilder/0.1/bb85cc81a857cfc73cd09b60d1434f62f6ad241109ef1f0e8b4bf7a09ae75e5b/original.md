```
is_mandatory(question::Question)
```

Check if a [`Question`](@ref) is mandatory.

# Examples

```julia-repl
julia> q = short_text_question("q1", "A question")
julia> is_mandatory(q)
false
```

```julia-repl
julia> q = short_text_question("q1", "A mandatory question", mandatory=true)
julia> is_mandatory(q)
true
```
