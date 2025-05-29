```
get_circuit_tuple(c::AbstractCircuit; include_reset::Bool = false)
```

回路 `c` に対応する回路タプルを返します。`include_reset` が `true` の場合はリセット層も含まれます。
