```
fg!(mod::Model)
```

Return function `fg!` of three arguments `(F, G, x)` as expected by Optim.jl.

## Remark

  * Returns anonymous function `(F, G, x) -> ...` (cf. [Optim.jl](https://github.com/JuliaNLSolvers/Optim.jl))
  * Depends on [Bb!](@ref Bb!) and [∂Bb!](@ref ∂Bb!).
