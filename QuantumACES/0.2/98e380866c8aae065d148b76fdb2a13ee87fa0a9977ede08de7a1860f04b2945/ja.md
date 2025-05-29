```
GateIndex
```

ゲートの異なるインデックスをすべて格納するオブジェクトです。

# フィールド

  * `gate::Gate`: ゲート。
  * `indices::Vector{Int32}`: ゲートの固有値または確率インデックス。
  * `pad_indices::Vector{Int32}`: パディングされたゲートの固有値または確率インデックス。
  * `marg_indices::Vector{Int32}`: マージナルゲートの固有値または確率インデックス。
  * `pad_marg_indices::Vector{Int32}`: パディングされたマージナルゲートの固有値または確率インデックス。
  * `rel_indices::Vector{Int32}`: 相対ゲートの固有値または確率インデックス。
  * `pad_rel_indices::Vector{Int32}`: パディングされた相対ゲートの固有値または確率インデックス。
