```
QuantumStateMinimumTimeProblem(traj, sys, obj, integrators, constraints; kwargs...)
QuantumStateMinimumTimeProblem(prob; kwargs...)
```

ターゲット状態に到達するための最小時間問題のための `DirectTrajOptProblem` を構築します。

# キーワード引数

  * `state_name::Symbol=:ψ̃`: 状態変数のためのシンボル。
  * `final_fidelity::Union{Real, Nothing}=nothing`: 最終的な忠実度。
  * `D=1.0`: 時間に対するコストの重み。
  * `piccolo_options::PiccoloOptions=PiccoloOptions()`: Piccoloのオプション。
