```
search_devices(; kwargs...) -> Vector{Dict{String, Any}}
```

すべてのAWS管理デバイスを検索し、`kwargs`を使用して結果をフィルタリングします。

有効な`kwargs`は次のとおりです：

  * `arns::Vector{String}`: 検索するデバイスのARN。
  * `names::Vector{String}`: 検索するデバイスの名前。
  * `types::Vector{String}`: 検索するデバイスの種類（例：QPUまたはシミュレーター）。
  * `statuses::Vector{String}`: 検索するデバイスのステータス（例：`"ONLINE"`または`"OFFLINE"`）。
  * `provider_names::Vector{String}`: 検索するデバイスのプロバイダー。
