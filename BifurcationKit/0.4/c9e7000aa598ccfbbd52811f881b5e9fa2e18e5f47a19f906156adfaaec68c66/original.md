```julia
struct EigArnoldiMethod{T, Tby, Tw, Tkw, vectype} <: BifurcationKit.AbstractIterativeEigenSolver
```

## Fields

  * `sigma::Any`: Shift for Shift-Invert method
  * `which::Any`: Which eigen-element to extract LR(), LM(), ...
  * `by::Any`: How do we sort the computed eigenvalues, defaults to real
  * `kwargs::Any`: Key words arguments passed to EigArpack
  * `x₀::Any`: Example of vector used for Krylov iterations

More information is available at [ArnoldiMethod.jl](https://github.com/haampie/ArnoldiMethod.jl). For example, you can pass the parameters `tol, mindim, maxdim, restarts`.

# Constructor

`EigArnoldiMethod(;sigma = nothing, which = ArnoldiMethod.LR(), x₀ = nothing, kwargs...)`
