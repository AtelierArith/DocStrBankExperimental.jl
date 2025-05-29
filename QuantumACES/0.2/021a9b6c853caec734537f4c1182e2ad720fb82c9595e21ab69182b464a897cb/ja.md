```
calc_memory_distances(c::AbstractCircuit; reset_type::Symbol = :meas_reset, max_event_set_size::Integer = 4, max_edge_degree::Integer = 2, explore_increasing_degree::Bool = false)
```

論理ZおよびXエラー距離を計算します。これは、シンドローム抽出回路`c`に対応するXおよびZメモリ回路に対応し、通常はそれぞれ垂直距離と水平距離です。リセットタイプは`reset_type`で指定され、`:meas_reset`または`:meas`にすることができます。Stimによって使用される検索パラメータは、`max_event_set_size`、`max_edge_degree`、および`explore_increasing_degree`です。
