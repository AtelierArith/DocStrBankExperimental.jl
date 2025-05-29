```
VelocityVerlet(; kwargs...)
```

Velocity Verletアルゴリズムのための時間積分ソルバー。ステップ数またはシミュレーションがカバーすべき時間のいずれかを指定します。

# キーワード

  * `time::Real`: シミュレーションがカバーする総時間。このキーワードが指定されると、キーワード`steps`はもはや許可されません。（オプション）
  * `steps::Int`: 計算された時間ステップの数。このキーワードが指定されると、キーワード`time`はもはや許可されません。（オプション）
  * `stepsize::Real`: 時間ステップのサイズを手動で指定します。（オプション）
  * `safety_factor::Real`: 安定性を確保するためのステップサイズの安全係数。（デフォルト: `0.7`）

!!! warning "時間ステップの指定"
    重要な時間ステップを手動で指定することは危険です！指定された時間ステップが高すぎてCFL条件が成り立たなくなると、シミュレーションは誤った結果を出し、クラッシュする可能性があります！


# 例外

  * `time`と`steps`の両方がキーワードとして指定された場合、エラーが発生します。
  * `time`も`steps`もキーワードとして指定されていない場合、エラーが発生します。
  * `safety_factor < 0`または`safety_factor > 1`の場合、エラーが発生します。

# 例

```julia-repl
julia> VelocityVerlet(steps=2000)
VelocityVerlet:
  n_steps        2000
  safety_factor  0.7

julia> VelocityVerlet(time=0.001)
VelocityVerlet:
  end_time       0.001
  safety_factor  0.7

julia> VelocityVerlet(steps=2000, stepsize=0.0001)
┌ Warning: stepsize specified! Please be sure that the CFD-condition holds!
└ @ Peridynamics ~/Code/Peridynamics.jl/src/time_solvers/velocity_verlet.jl:66
VelocityVerlet:
  n_steps        2000
  Δt             0.0001
  safety_factor  0.7
```
