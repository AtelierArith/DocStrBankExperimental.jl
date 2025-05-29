```
setup_table!(config, data, ::Val{:nominal_load})
```

負荷テーブルを設定します。

また、以下を呼び出します：

  * [`shape_nominal_load!(config, data)`](@ref) - 任意の地域による時間ごとの負荷プロファイルで時間ごとの負荷電力をスケーリングします
  * [`match_nominal_load!(config, data)`](@ref) - 任意の地域による年間負荷エネルギーを一致させます
  * [`add_nominal_load!(config, data)`](@ref) - 任意の地域による時間ごとの負荷電力を追加します
