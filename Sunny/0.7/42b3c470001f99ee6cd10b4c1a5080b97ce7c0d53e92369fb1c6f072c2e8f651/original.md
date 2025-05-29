```
minimize_energy!(sys::System{N}; maxiters=1000, method=Optim.ConjugateGradient(),
                 kwargs...) where N
```

Optimizes the spin configuration in `sys` to minimize energy. A total of `maxiters` iterations will be attempted. The `method` parameter will be used in the `optimize` function of the [Optim.jl package](https://github.com/JuliaNLSolvers/Optim.jl). Any remaining `kwargs` will be included in the `Options` constructor of Optim.jl.
