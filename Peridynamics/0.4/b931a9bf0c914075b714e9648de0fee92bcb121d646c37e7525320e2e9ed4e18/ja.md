```
DynamicRelaxation(; kwargs...)
```

準静的シミュレーションに使用される適応動的緩和アルゴリズムのための時間積分ソルバー。

# キーワード

  * `steps::Int`: 計算された時間ステップの数。このキーワードが指定されると、キーワード `time` はもはや許可されません。
  * `stepsize::Real`: 時間ステップのサイズを手動で指定します。（デフォルト: `1.0`）
  * `damping_factor::Real`: 質量行列の値を増加させるための減衰係数。（デフォルト: `1.0`）

# 例外

  * `steps < 0` の場合、エラーが発生します。
  * `stepsize < 0` の場合、エラーが発生します。
  * `damping_factor < 0` の場合、エラーが発生します。

# 例

```julia-repl
julia> DynamicRelaxation(steps=1000)
DynamicRelaxation:
  n_steps  1000
  Δt       1
  Λ        1

julia> DynamicRelaxation(steps=1000, damping_factor=2)
DynamicRelaxation:
  n_steps  1000
  Δt       1
  Λ        2
```
