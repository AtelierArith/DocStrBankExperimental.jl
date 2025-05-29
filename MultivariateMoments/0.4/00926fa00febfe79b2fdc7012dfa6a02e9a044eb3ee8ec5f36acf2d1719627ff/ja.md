```
struct AlgebraicFallbackBorderSolver{
    M<:Union{Nothing,SS.AbstractMultiplicationMatricesSolver},
    S<:AlgebraicBorderSolver,
}
    multiplication_matrices_solver::M
    algebraic_solver::S
end
```

`multiplication_matrices_solver`を使って解決し、失敗した場合は`algebraic_solver`を使って境界基底によって形成された代数系を解決します。
