```
HydroRoute{N} <: AbstractHydroRoute
```

カスタマイズ可能なフラックス方程式を使用した水文学的ルーティングコンポーネントを表します。

# フィールド

  * `rfluxes::Vector{<:AbstractFlux}`: ルーティングプロセスを定義するフラックス関数（例：流出計算）。
  * `multi_flux_func::Function`: すべての非状態導関数フラックスを評価するためのコンパイル済み関数。
  * `multi_ode_func::Function`: ODEソルバーによって使用される状態導関数のためのコンパイル済み関数。
  * `aggr_func::Function`: 接続された要素間でフローを集約または分配するための関数（しばしば恒等関数または行列乗算）。
  * `infos::NamedTuple`: メタデータ（入力、出力、状態、パラメータ、nns）。

# コンストラクタ

```julia
HydroRoute(; rfluxes, dfluxes, aggr_func, name=nothing)
```

  * `rfluxes`: ルーティングフラックスのベクター（例：`HydroFlux`、`NeuralFlux`）。
  * `dfluxes`: 状態導関数フラックスのベクター（`StateFlux`）。
  * `aggr_func`: 集約/分配関数。
  * `name`: オプションのシンボル識別子。

# 注意事項

  * 効率的な計算のために特化した関数（`multi_flux_func`、`multi_ode_func`）を構築します。
  * より大きなモデル（例：`HydroModel`）内での使用を目的としています。
  * 変数管理とメタデータ追跡を内部で処理します。
