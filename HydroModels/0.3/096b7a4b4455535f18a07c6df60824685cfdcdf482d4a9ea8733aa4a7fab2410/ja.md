```
(route::RapidRoute)(input::Array, params::ComponentVector; kwargs...)
```

RAPIDルーティングシミュレーションを実行します。

# 引数

  * `input::Array`: 横方向の流入データ、通常の形状は (1, nodes, timesteps) で、変数は流入です。
  * `params::ComponentVector`: 各ノードのための `:rapid_k` と `:rapid_x` を含むパラメータ。

# キーワード引数

  * `delta_t::Float64`: シミュレーションの時間ステップ（秒単位、デフォルト: 1.0）。
  * `device`: 計算デバイス（例: CPU のための `identity`、`gpu` 関数）。デフォルトは `identity`。
  * `ptyidx`: パラメータをノードにマッピングするインデックス。デフォルトは `1:num_nodes`。
  * `interp`: 時間変動入力のための補間方法。デフォルトは `DirectInterpolation`。
  * `solver`: ODEソルバーインスタンス。デフォルトは `ManualSolver(mutable=true)`。
  * `timeidx`: シミュレーションのための時間インデックス。デフォルトは `1:time_len`。
  * `initstates`: 初期放流値。デフォルトはゼロ。

# 戻り値

  * `AbstractArray{T,3}`: 放流の出力配列、形状は (1, nodes, timesteps)。

# 例

```julia
# 'rapid_route' が RapidRoute インスタンスであると仮定
discharge = rapid_route(lateral_inflow, parameters; delta_t=3600.0)
```

# 注意事項

  * 行列ベースのアプローチを使用して Muskingum-Cunge 方程式を解決します。
  * `k`、`x`、および `delta_t` に基づいて内部的に Muskingum 係数 (c0, c1, c2) を計算します。
  * `input` は 3D である必要があります（変数、ノード、時間）。
