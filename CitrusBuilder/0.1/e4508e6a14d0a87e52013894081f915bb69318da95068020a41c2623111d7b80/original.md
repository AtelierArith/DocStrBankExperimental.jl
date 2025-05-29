```
has_response_options(questions::Question)
```

Check if a [`Question`](@ref) has any response options.

# Examples

```julia-repl
julia> q = five_point_choice_question("q1", "A question")
julia> has_response_options(q)
false
```

```julia-repl
julia> options = response_scale([response_option("o1", "option 1")])
julia> q = dropdown_list_question("q1", "A dropdown question", options)
julia> has_response_options(q)
true
```
