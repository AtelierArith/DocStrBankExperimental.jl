```
struct EmissionsProcess{T} <: EmissionsData{T}

EmissionsProcess(emissions::Dict{<:ResourceEmit,T}) where T
EmissionsProcess(emissions::Dict{<:ResourceEmit,T}, _) where T
EmissionsProcess()
```

キャプチャはありませんが、プロセス排出は存在します。`co2_capture`を入力として必要としませんが、提供された場合は受け入れ、無視します。

# フィールド

  * **`emissions::Dict{ResourceEmit, T}`**: 生産された単位あたりの排出量。
