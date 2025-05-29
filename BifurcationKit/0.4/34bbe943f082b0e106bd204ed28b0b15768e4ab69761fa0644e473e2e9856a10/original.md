```julia
mutable struct KrylovLSInplace{F, K, Tl, Tr} <: BifurcationKit.AbstractIterativeLinearSolver
```

Create an inplace linear solver based on [Krylov.jl](https://jso.dev/Krylov.jl). Can be used to solve `(a₀ * I + a₁ * J) * x = rhs`.

The Krylov space is pre-allocated. This is really great for GPU but also for CPU.

## Fields

  * `workspace::Any`: Can be Krylov.GmresWorkspace for example
  * `KrylovAlg::Symbol`: Krylov method
  * `kwargs::Any`: Arguments passed to the linear solver
  * `Pl::Any`: Left preconditioner
  * `Pr::Any`: Right preconditioner
  * `is_inplace::Bool`: Is the linear mapping inplace
