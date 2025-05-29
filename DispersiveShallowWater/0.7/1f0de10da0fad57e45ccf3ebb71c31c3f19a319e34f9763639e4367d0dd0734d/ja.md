```
initial_condition_soliton(x, t, equations::HyperbolicSerreGreenNaghdiEquations1D, mesh)
```

周期的な領域での収束テストに使用される[`SerreGreenNaghdiEquations1D`](@ref)のソリトン解です。これは物理的には[`SerreGreenNaghdiEquations1D`](@ref)の[`initial_condition_convergence_test`](@ref)と同じです。これは[`HyperbolicSerreGreenNaghdiEquations1D`](@ref)の正確な解ではないことに注意してください（緩和パラメータ$\lambda \to \infty$の限界においてのみ）。

また、[`initial_condition_convergence_test`](@ref)も参照してください。
