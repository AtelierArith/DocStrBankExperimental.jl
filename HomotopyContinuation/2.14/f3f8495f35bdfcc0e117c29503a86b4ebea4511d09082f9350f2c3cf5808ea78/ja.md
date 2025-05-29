```
TrackerOptions(; options...)
```

[`Tracker`](@ref)のオプションのセット。

## オプション

  * `automatic_differentiation = 1`: 値 `automatic_differentiation` は、自動微分を使用して導関数が計算される順序を決定します。そうでなければ数値微分が使用されます。自動微分は追加のコンパイル時間を要しますが、数値的に困難な経路に対しては `automatic_differentiation = 3` を使用することを強く推奨します。
  * `max_steps = 10_000`: トラッカーが試みる最大ステップ数
  * `max_step_size = Inf`: ステップの最大サイズ
  * `max_initial_step_size = Inf`: 最初のステップの最大サイズ
  * `min_step_size = 1e-48`: 最小ステップサイズ。より小さいステップサイズが必要な場合、トラッキングは終了します。
  * `extended_precision = true`: 必要に応じて、一部の計算で拡張精度の使用を許可するかどうか。これにより、数値的に困難な経路を追跡する能力が大幅に向上する可能性があります。
  * `terminate_cond = 1e13`: 相対成分ごとの条件数 `cond(H_x, ẋ)` が `terminate_cond` より大きい場合、経路は条件が悪すぎるとして終了します。
  * `parameters::Union{Symbol,TrackerParameters} = :default` [`TrackerParameters`](@ref) を設定して、経路追跡アルゴリズムの性能を制御します。値 `:default`、`:conservative` および `:fast` は、それぞれ [`DEFAULT_TRACKER_PARAMETERS`](@ref)、[`CONSERVATIVE_TRACKER_PARAMETERS`](@ref)、および [`FAST_TRACKER_PARAMETERS`](@ref) を使用するためのショートハンドです。
