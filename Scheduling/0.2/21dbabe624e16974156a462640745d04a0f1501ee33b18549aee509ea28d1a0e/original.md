```
Jobs(P::Array{Rational{Int}, 1})
```

Generates a set of jobs with basic processing times determined by the `P` array, denoted by `J_1`, `J_2`, etc.

# Example

```julia-repl
julia> Jobs([1//2, 3, 5//3, 7])
A set of 4 job(s):
​    Job J_1:    [p = 1//2]
    Job J_2:    [p = 3]
    Job J_3:    [p = 5//3]
    Job J_4:    [p = 7]

```
