```
QuadraticOTNewton(;θ = 0.1, κ = 0.5, δ = 1e-5, armijo_max = 50)
```

Semi-smooth Newton method (Algorithm 2 of Lorenz et al. 2019) with Armijo parameters `θ` and `κ`, and conjugate gradient regularisation `δ`.  `armijo_max` sets the maximum number of Armijo step size trials.

See also: [`QuadraticOTNewton`](@ref), [`quadreg`](@ref)
