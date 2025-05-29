```
shadow_document_property_update_callback(value)
```

シャドウドキュメントのプロパティが更新された直後に呼び出されるコールバック。コールバックが呼び出されるとき、親 [`ShadowFramework`](@ref) はロックされます。このロックは再入可能です。

引数:

  * `value (Any)`: シャドウドキュメント内のプロパティの新しい値。
