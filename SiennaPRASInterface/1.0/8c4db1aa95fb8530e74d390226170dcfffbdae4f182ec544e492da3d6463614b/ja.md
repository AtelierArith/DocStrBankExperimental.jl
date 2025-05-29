```
generate_pras_system(sys_location::String, aggregation; kwargs...)
```

Sienna/Data PowerSystemsのシステムJSONファイルからPRAS SystemModelを生成します。

# 引数

  * `sys_location::String`: Sienna/Data PowerSystemsシステムJSONファイルの場所
  * `aggregation::Type{AT}`: 集約トポロジータイプ
  * `lump_region_renewable_gens::Bool`: 地域再生可能発電機の集約
  * `export_location::Union{Nothing, String}`: .prasファイルのエクスポート先

# 戻り値

  * `PRASCore.SystemModel`: PRAS SystemModel
