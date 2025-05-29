```
ProducerBlueprint
```

  * type_id::UUID - ブループリントのタイプID。
  * name::String - ブループリント名。
  * lifecycle::Restorable - ブループリントのライフサイクル。
  * batch_res::Dict{<:Blueprint,Int64} - 生産バッチに必要なリソース。これらは生産中に破壊されます。
  * batch_tools::Dict{<:Blueprint,Int64} - 生産バッチに必要なツール。これらは生産中に使用されます。
  * batch::Dict{<:Blueprint,Int64} - バッチごとの出力。
