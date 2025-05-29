```
initial_condition_soliton(x, t, equations::HyperbolicSerreGreenNaghdiEquations1D, mesh)
```

A soliton solution of the [`SerreGreenNaghdiEquations1D`](@ref) used for convergence tests in a periodic domain. This is physically the same as [`initial_condition_convergence_test`](@ref) for the [`SerreGreenNaghdiEquations1D`](@ref). Please note that this is not an exact solution of the [`HyperbolicSerreGreenNaghdiEquations1D`](@ref) (only in the limit of the relaxation parameter $\lambda \to \infty$).

See also [`initial_condition_convergence_test`](@ref).
