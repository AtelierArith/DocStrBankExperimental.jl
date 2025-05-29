```
struct AlgebraicFallbackBorderSolver{
    M<:Union{Nothing,SS.AbstractMultiplicationMatricesSolver},
    S<:AlgebraicBorderSolver,
}
    multiplication_matrices_solver::M
    algebraic_solver::S
end
```

Solve with `multiplication_matrices_solver` and if it fails, falls back to solving the algebraic system formed by the border basis with `algebraic_solver`.
