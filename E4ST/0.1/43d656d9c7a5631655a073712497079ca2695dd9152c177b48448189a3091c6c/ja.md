```
update_build_status!(config, data, table_name)
```

シミュレーションで構築されたジェネレーターの build_status を変更します。

  * `unbuilt -> new` もし `last(pcap)` が閾値を超えた場合
  * `built -> retired_exog` もし `year_shutdown` を超えて退役した場合
  * `built -> retired_endog` もし `year_shutdown` 前に退役した場合
