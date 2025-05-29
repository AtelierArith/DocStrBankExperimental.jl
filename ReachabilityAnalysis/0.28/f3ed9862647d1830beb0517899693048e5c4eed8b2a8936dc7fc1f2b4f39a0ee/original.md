```
normalize(ivp::InitialValueProblem)
```

Transform an initial-value problem into a normalized (or canonical) form.

### Input

  * `ivp` – initial-value problem

### Output

Either the same initial-value problem if it already conforms to a canonical form, or a new one otherwise.

### Notes

This function extends [`normalize`](@ref normalize(::AbstractSystem)) for initial-value problems.
