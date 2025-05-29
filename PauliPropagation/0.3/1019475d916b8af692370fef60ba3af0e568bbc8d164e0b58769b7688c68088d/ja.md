```
getparameterindices(circuit, ::PauliRotation, gate_symbols::Vector{Symbol}), qinds::Vector{Int})
```

`PauliRotation` ゲートのパラメータインデックスを取得するユーティリティ関数で、シンボル `gate_symbols` が量子ビット `qinds` に作用します。例えば、`getparameterindices(circuit, PauliRotation, [:X], [1])` のように使用します。
