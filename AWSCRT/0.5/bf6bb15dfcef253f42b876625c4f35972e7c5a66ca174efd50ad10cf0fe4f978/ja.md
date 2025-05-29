```
shadow_document_property_pre_update_function(shadow_document::AbstractDict, key::String, value)::Bool
```

シャドウドキュメントのプロパティを更新する際に呼び出される関数です。これにより、特定のプロパティに対してカスタム更新動作を実装したい場合に、このパッケージ内の更新動作を置き換えることができます。この関数が呼び出されると、親 [`ShadowFramework`](@ref) はロックされます。ロックは再入可能です。

```
!!! warning "警告"
    この関数は指定された `key` のみを更新できます。この関数は `shadow_document` 内の他のプロパティを変更することはできません。
```

引数:

  * `shadow_document (AbstractDict)`: 更新されるシャドウドキュメント。
  * `key (String)`: 更新される値のための `shadow_document` 内のキー。
  * `value (Any)`: `key` の新しい値。

更新が行われたかどうかを示す `Bool` を返します。
