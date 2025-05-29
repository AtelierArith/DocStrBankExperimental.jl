```
fgh!(mod::Model)
```

Return function `fgh!` of four arguments `(F, G, H, x)` as expected by Optim.jl.

## Remark

  * Returns anonymous function `(F, G, H, x) -> ...` (cf. [Optim.jl](https://github.com/JuliaNLSolvers/Optim.jl))
  * Depends on [Bb!](@ref Bb!), [∂Bb!](@ref ∂Bb!) and [∂∂Bb!](@ref ∂∂Bb!).
