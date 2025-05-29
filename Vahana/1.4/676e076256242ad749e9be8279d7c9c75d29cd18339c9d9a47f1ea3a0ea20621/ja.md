```
read_metadata(sim::Simulation, type::Union{Symbol, DataType}[, field::Symbol, key::Symbol ])
read_metadata(filename::String, type::Union{Symbol, DataType}[, field::Symbol, key::Symbol ])
```

エージェントタイプまたはエッジタイプの`field`、または`globals`または`params`構造体のメタデータを読み取ります（[`create_simulation`](@ref）を参照）またはラスターに対して（この場合、`field`はラスターの名前でなければなりません）。`type`はエージェントタイプまたはエッジタイプ、またはこれらのシンボルのいずれかでなければなりません: :Global, :Param または :Raster。メタデータは`key, value`ペアを介して保存されます。複数のペアを単一のフィールドに添付することができ、メタデータの単一の部分は`key`パラメータを介して取得できます。これが設定されていない場合（またはSymbol()に設定されている場合）、このフィールドの完全なメタデータを持つDict{Symbol, Any}が返されます。`field`も設定されていない場合、すべてのフィールドのメタデータが返されます。

参照: [`write_metadata`](@ref)
