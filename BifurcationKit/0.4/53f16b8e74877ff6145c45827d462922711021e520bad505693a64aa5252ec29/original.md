```julia
mutable struct KrylovLS{K, Tl, Tr} <: BifurcationKit.AbstractIterativeLinearSolver
```

Create a linear solver based on [Krylov.jl](https://jso.dev/Krylov.jl). Can be used to solve `(a₀ * I + a₁ * J) * x = rhs`. You have access to `cg, cr, gmres, symmlq, cg_lanczos, cg_lanczos_shift_seq`...

## Fields

  * `KrylovAlg::Symbol`: Krylov method
  * `kwargs::Any`: Arguments passed to the linear solver
  * `Pl::Any`: Left preconditioner
  * `Pr::Any`: Right preconditioner

## Other methods

Look at `KrylovLSInplace` for a method where the Krylov space is kept in memory
