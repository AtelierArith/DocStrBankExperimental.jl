```
write_metadata(sim::Simulation, type::Union{Symbol, DataType}, field::Symbol, key::Symbol, value)
```

エージェントタイプまたはエッジタイプの`field`、または`globals`や`params`構造体（[`create_simulation`](@ref)を参照）にメタデータを添付します。また、ラスタに対してもメタデータを添付できます（この場合、`field`はラスタの名前でなければなりません）。`type`はエージェントタイプまたはエッジタイプ、またはこれらのシンボルのいずれかである必要があります: :Global, :Param または :Raster。メタデータは`key, value`ペアを介して保存されるため、単一のフィールドに複数のメタデータを添付できます。

参照: [`read_metadata`](@ref)
