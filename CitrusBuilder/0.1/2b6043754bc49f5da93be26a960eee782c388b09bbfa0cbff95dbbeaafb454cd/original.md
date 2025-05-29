```
attributes(question::Question)
```

Get the attributes of a [`Question`](@ref).

# Examples

```julia-repl
julia> q = numerical_input("q1", "A numerical input", minimum=0, maximum=10)
julia> attributes(q)
Dict{String, Any} with 2 entries:
  "min_num_value_n" => 0
  "max_num_value_n" => 10
```
