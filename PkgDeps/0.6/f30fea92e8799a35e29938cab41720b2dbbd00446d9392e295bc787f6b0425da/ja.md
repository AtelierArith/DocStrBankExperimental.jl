```
reachable_registries(registry_names::Array)
reachable_registries(registry_name::String; depots::Union{String, Vector{String}}=Base.DEPOT_PATH)
reachable_registries(; depots::Union{String, Vector{String}}=Base.DEPOT_PATH)
```

見つかったレジストリの配列を取得します。

# 引数

  * `registry_names::Array`: 取得するレジストリのリスト

# キーワード

  * `depots::Union{String, Vector{String}}=Base.DEPOT_PATH`: レジストリを探すためのデポ

# 戻り値

  * `Array{RegistryInstance}`: 見つかったすべてのレジストリのリスト
