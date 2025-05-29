```
(route::HydroRoute)(input::AbstractArray{T,3}, params::ComponentVector; kwargs...)
```

`HydroRoute`コンポーネントのシミュレーションを実行します。

# 引数

  * `input::AbstractArray{T,3}`: 形状 (variables, nodes, timesteps) の入力データ配列。
  * `params::ComponentVector`: ルーティングフラックスのためのパラメータ。

# キーワード引数

  * `initstates`: コンポーネントの初期状態。デフォルトはゼロ。
  * `ptyidx`: パラメータをノードにマッピングするインデックス。デフォルトは `1:num_nodes`。
  * `styidx`: 状態をノードにマッピングするインデックス。デフォルトは `1:num_nodes`。
  * `interp`: 時間変化する入力のための補間方法（例: `DirectInterpolation`）。
  * `solver`: ODEソルバーインスタンス（例: `ManualSolver`）。
  * `timeidx`: シミュレーションのための時間インデックス。デフォルトは `1:time_len`。
  * `device`: 計算デバイス（例: CPUの場合は `identity`）。

# 戻り値

  * `AbstractArray`: 状態の進化と計算されたフラックスを含む出力配列、形状 (output_variables, nodes, timesteps)。

# 例

```julia
# 'route'がHydroRouteインスタンスであると仮定
output = route(input_data, parameters; solver=Tsit5())
```

# 注意事項

  * 3D入力（variables, nodes, timesteps）を期待します。
  * 指定されたソルバーを使用して状態変数を時間的に統合します。
  * 入力と状態に基づいて出力を計算するために `multi_flux_func` を適用します。
