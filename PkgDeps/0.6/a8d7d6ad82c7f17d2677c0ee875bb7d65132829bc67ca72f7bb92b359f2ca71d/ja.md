```
users(uuid::UUID; registries::Array{RegistryInstance}=reachable_registries())
users(pkg_name::String, pkg_registry_name::String=GENERAL_REGISTRY; kwargs...)
users(pkg_name::String, pkg_registry::RegistryInstance; kwargs...))
```

与えられたパッケージのユーザーを見つけます。

# 引数

  * `uuid::UUID`: パッケージのUUID。
  * `pkg_name::String`: このパッケージのユーザーを見つけます。
  * `pkg_registry_name::String="General"`: `pkg_name`が登録されているレジストリの名前。これは`pkg_name`のUUIDを検索するために使用されます。

# キーワード

  * `registries::Array{RegistryInstance}=reachable_registries()`: ユーザーを検索するためのレジストリ。

# 戻り値

  * `Array{String}`: 与えられたパッケージに依存しているすべてのパッケージ。
