```
FCIQMC(; kwargs...) <: PMCAlgorithm
```

フル構成相互作用量子モンテカルロ（FCIQMC）法のアルゴリズム。デフォルトのアルゴリズムは[`ProjectorMonteCarloProblem`](@ref)です。

# キーワード引数とデフォルト：

  * `shift_strategy = DoubleLogUpdate(; targetwalkers = 1_000, ζ = 0.08,   ξ = ζ^2/4)`: `shift`をどのように更新するか。
  * `time_step_strategy = ConstantTimeStep()`: 時間ステップを調整するかどうか。

他に[`ProjectorMonteCarloProblem`](@ref)、[`ShiftStrategy`](@ref)、[`TimeStepStrategy`](@ref)、[`DoubleLogUpdate`](@ref)、[`ConstantTimeStep`](@ref)を参照してください。
