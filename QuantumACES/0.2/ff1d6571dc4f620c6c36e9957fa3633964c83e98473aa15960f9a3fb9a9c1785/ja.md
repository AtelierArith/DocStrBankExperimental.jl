```
get_tuple_set_data(c::AbstractCircuit; error_target::Real = 0.1, add_circuit::Bool = false)
get_tuple_set_data(c::AbstractCircuit, tuple_set::Vector{Vector{Int}}; error_target::Real = 0.1, add_circuit::Bool = false)
```

回路 `c` に対応するタプルセットデータを返します。非重複タプルは、提供された `tuple_set` か、`c` の基本タプルセットのいずれかです。重複数は、レイヤー内のゲートの平均ノイズに反比例して初期化され、経験則的におおよそエラー率 `error_target` をターゲットにします。また、`add_circuit` が `true` の場合、元の回路が重複タプルに追加されます。

重複タプルは、測定に効率的な奇数の重複数（同じ回路レイヤーを何度も繰り返す場合など）を持つ順序2（パウリまで）を使用するのが最適であり、そうでない場合（例えば、シンドローム抽出回路など）は偶数の重複数を使用するのが良いようです。
