```
AbstractSeqRegistrar{T <: Integer}
```

連続整数IDを使用する[`AbstractRegistrar`](@ref)のサブタイプです。次に利用可能なIDを返し、内部カウンター（`next_id`と呼ばれる）を1つ増やすヘルパー関数[`_nextid!`](@ref)が付属しています。他の内部状態の変更は、各サブタイプのための`get_id!` API関数メソッドによって処理されるべきです。

実装については、[`SimpleRegistrar`](@ref)、[`LineageRegistrar`](@ref)、および[`LineageCoordRegistrar`](@ref)を参照してください。
