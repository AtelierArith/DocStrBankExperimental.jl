```
optimise_repetitions(c::AbstractCircuit, tuple_set_data::TupleSetData; options::OptimOptions = OptimOptions())
```

回路 `c` に対して提供されたタプルセットデータ `tuple_set_data` の繰り返し数を最適化した後、タプルセットデータを返します。最適化は [`OptimOptions`](@ref) オブジェクト `options` によってパラメータ化されています。
