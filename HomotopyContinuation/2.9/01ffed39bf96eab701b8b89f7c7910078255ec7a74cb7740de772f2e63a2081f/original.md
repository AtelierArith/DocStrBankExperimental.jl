```
square_up(F::Union{System, AbstractSystem}; identity_block = true, compile = compile = mixed)
```

Creates the [`RandomizedSystem`](@ref) $\mathfrak{R}(F(x); N)$ where $N$ is the number of variables of `F`.
