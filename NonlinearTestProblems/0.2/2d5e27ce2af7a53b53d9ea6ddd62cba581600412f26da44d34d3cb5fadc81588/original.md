`root(problem)`

Root (solution) of a test problem. Formally,

```julia
problem(root(problem)) ≈ zeros(range_dimension(problem))
```

Problems are guaranteed to have a unique root.
