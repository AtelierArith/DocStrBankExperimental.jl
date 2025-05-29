```
optimize(
    fdf, x₀;
    method,
    kw...
)
```

Find an optimizer for `fdf`, starting with the initial approximation `x₀`.     `method` keyword chooses a specific optimization method. See [`optimize!`](@ref) for     the description of other keywords.
