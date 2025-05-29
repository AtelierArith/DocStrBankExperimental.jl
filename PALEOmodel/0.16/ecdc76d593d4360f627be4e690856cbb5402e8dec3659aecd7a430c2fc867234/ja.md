```
FieldRecord{FieldData <: AbstractData, Space <: AbstractSpace, V, N, Mesh <: AbstractMeshOrNothing, R}
FieldRecord(dataset, f::PB.Field, attributes; [sizehint=nothing])
```

`PALEOboxes.Field{FieldData, Space, N, V, Mesh}` からの値を含む `records::R` の一連。

保存された値にアクセスするには：

  * [`FieldArray`](@ref) として、[`FieldArray(fr::FieldRecord)`](@ref) または [`get_array`](@ref) を使用します。
  * スカラー データのみの場合、`PALEOboxes.get_data` を使用してベクトルとして取得します。

# 実装

`records::R` のストレージは内部形式であり、次のような最適化がある場合があります：

  * 単一の `values` を持つフィールドを `eltype(Field.values)` のベクトルとして保存する最適化、配列 `values` を持つフィールドは `records` に配列のベクトルとして保存されます。
  * 線形ベクトルとして保存された空間的な直交グリッド（例：`mesh` isa `PALEOboxes.Grids.CartesianLinearGrid`）
