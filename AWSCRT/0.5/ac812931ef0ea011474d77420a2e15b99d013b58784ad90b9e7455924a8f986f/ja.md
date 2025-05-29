```
shadow_document_pre_update_callback(state::Dict{String,Any})
```

シャドウドキュメントが更新される前に呼び出されるコールバック。コールバックが呼び出されるとき、親の [`ShadowFramework`](@ref) はロックされません。

引数:

  * `state (Dict{String,Any})`: 受信したシャドウ状態。これは報告された状態またはデルタ状態である可能性があります。
