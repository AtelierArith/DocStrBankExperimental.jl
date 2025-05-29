```
Jobs(P::Array{Int, 1})
```

Generates a set of jobs with basic processing times determined by the `P` array, denoted by `J_1`, `J_2`, etc.

# Example

```julia-repl
julia> Jobs([1, 5, 6, 2])
A set of 4 job(s):
    Job J_1:    [p = 1]
    Job J_2:    [p = 5]
    Job J_3:    [p = 6]
    Job J_4:    [p = 2]

```
