```
generate_temporal_structure!(m)
```

与えられたSpineOptモデルのために時間構造を生成します。その後、生成された構造を照会するために以下の関数を呼び出すことができます：

  * `time_slice`
  * `t_before_t`
  * `t_in_t`
  * `t_in_t_excl`
  * `t_overlaps_t`
  * `to_time_slice`
  * `current_window`
