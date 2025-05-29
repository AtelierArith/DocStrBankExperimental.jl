```
SSFloquetEffectiveLiouvillian(steadystate_solver = SteadyStateDirectSolver())
```

[`steadystate_fourier`](@ref) を解くソルバーで、まず効果的な時間非依存のリウビリアンを抽出し、その後 `steadystate_solver` を使用して定常状態を抽出します。

# パラメータ

  * `steadystate_solver::SteadyStateSolver=SteadyStateDirectSolver()`: 効果的なリウビリアンに使用するソルバー。

!!! note
    このソルバーは [`steadystate_fourier`](@ref) のみで利用可能です。

