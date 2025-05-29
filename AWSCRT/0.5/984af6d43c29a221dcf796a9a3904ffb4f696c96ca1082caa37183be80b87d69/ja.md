```
shadow_document_post_update_callback(shadow_document::AbstractDict)
```

シャドウドキュメントが更新された後に呼び出されるコールバックです。このコールバックが呼び出されるとき、親 [`ShadowFramework`](@ref) はロックされません。これは、シャドウドキュメントをディスクに永続化するのに適した場所です。

引数:

  * `shadow_document (AbstractDict)`: 更新されたシャドウドキュメント。
