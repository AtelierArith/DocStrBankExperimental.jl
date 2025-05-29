```julia
struct EigArpack{T, Tby, Tw} <: BifurcationKit.AbstractIterativeEigenSolver
```

Create an eigen solver based on [Arpack.jl](https://github.com/JuliaLinearAlgebra/Arpack.jl).

## Fields

  * `sigma::Any`: Shift for Shift-Invert method with `(J - sigma⋅I)
  * `which::Symbol`: Which eigen-element to extract :LR, :LM, ...
  * `by::Any`: Sorting function, default to real
  * `kwargs::Any`: Keyword arguments passed to EigArpack

# Constructor

`EigArpack(sigma = nothing, which = :LR; kwargs...)`

More information is available at [Arpack.jl](https://github.com/JuliaLinearAlgebra/Arpack.jl). You can pass the following parameters `tol = 0.0, maxiter = 300, ritzvec = true, v0 = zeros((0,))`.
