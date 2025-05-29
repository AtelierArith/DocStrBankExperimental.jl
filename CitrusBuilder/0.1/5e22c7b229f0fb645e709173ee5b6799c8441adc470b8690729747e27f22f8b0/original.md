```
has_subquestions(question::Question)
```

Check if a [`Question`](@ref) has any subquestions.

# Examples

```julia-repl
julia> q = short_text_question("q1", "A question")
julia> has_subquestions(q)
false
```

```julia-repl
julia> q = multiple_short_text_question("q1", "Multiple questions") do
    subquestion("sq1", "subquestion 1"),
    subquestion("sq2", "subquestion 2")
end
julia> has_subquestions(q)
true
```
