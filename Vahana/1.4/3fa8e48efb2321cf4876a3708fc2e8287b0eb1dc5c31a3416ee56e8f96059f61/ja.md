```
read_sim_metadata(sim::Simulation, [ key::Symbol = Symbol() ])
read_sim_metadata(filename::String, [ key::Symbol = Symbol() ])
```

シミュレーションまたはファイル `filename` からメタデータを読み取ります。メタデータは `key`、値のペアで保存されます。`key` が設定されていない場合（または Symbol() に設定されている場合）、シミュレーションの完全なメタデータを含む Dict{Symbol, Any} が返されます。

以下のメタデータは自動的に保存されます：

  * simulation_name
  * model_name
  * date (フォーマット "yyyy-mm-dd hh:mm:ss")

参照： [`write_metadata`](@ref)
