```
steadystate(model::BSTModel; tspan::Tuple{Float64,Float64} = (0.0,20.0), Δt::Float64 = 0.01, input::Union{Nothing,Function} = nothing) -> Array{Float64,1}
```

`steadystate` 関数は、`build` 関数を使用して構築されたモデルオブジェクトの定常状態を評価するために使用されます。

### 引数

  * `model::BSTModel`: `build` 関数を使用して構築されたモデルオブジェクト。
  * `tspan::Tuple{Float64,Float64}`: シミュレーションの時間範囲を定義するタプル。デフォルトは `(0.0,20.0)` です。
  * `Δt::Float64`: シミュレーションの時間ステップ。デフォルトは `0.01` です。
  * `input::Union{Nothing,Function}`: シミュレーションを駆動するために使用できるオプションの入力関数。デフォルトは `nothing` です。

### 戻り値

  * システムの定常状態を表す状態値のベクトル。
