```
optimise_design(c::AbstractCircuit; options::OptimOptions = OptimOptions())
optimise_design(c::AbstractCircuit, tuple_set_data::TupleSetData; options::OptimOptions = OptimOptions())
```

回路 `c` に対して、タプルセットデータ `tuple_set_data` で初期化された最適化された実験デザインを返します。最適化は [`OptimOptions`](@ref) オブジェクト `options` によってパラメータ化されています。
