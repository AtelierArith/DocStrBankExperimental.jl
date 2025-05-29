```
get_devices(; kwargs...) -> Vector{AwsDevice}
```

フィルター `kwargs` を満たすすべての AWS デバイスを返します。デバイスのプロパティは設定されており、地域に適した `AWSConfig` が添付されています。

有効な `kwargs` は次のとおりです：

  * `arns::Vector{String}`: 検索するデバイスの ARN。
  * `names::Vector{String}`: 検索するデバイスの名前。
  * `types::Vector{String}`: 検索するデバイスの種類（例：QPUまたはシミュレーター）。
  * `statuses::Vector{String}`: 検索するデバイスのステータス（例：`"ONLINE"` または `"OFFLINE"`）。
  * `provider_names::Vector{String}`: 検索するデバイスのプロバイダー。
  * `order_by::String`: デバイスをソートするために使用されるプロパティ。デフォルトは `"name"` です。
