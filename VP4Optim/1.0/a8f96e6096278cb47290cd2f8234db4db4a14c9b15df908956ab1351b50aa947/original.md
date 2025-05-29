```
f(mod::Model)
```

Return function `f` of argument `x` to be minimized, as expected by Optim.jl

## Remark

  * Returns anonymous function `x -> ...` (cf. [Optim.jl](https://github.com/JuliaNLSolvers/Optim.jl))
  * Depends on [Bb!](@ref Bb!).
