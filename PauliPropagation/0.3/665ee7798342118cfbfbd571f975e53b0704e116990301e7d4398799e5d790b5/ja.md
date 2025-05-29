```
getparameterindices(circuit, ::PauliRotation, gate_symbols::Vector{Symbol}))
```

`PauliRotation` ゲートのパラメータインデックスをシンボル `gate_symbols` で取得するためのユーティリティ関数。例えば、`getparameterindices(circuit, PauliRotation, [:X])`。
