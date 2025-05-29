```
removetarget!(node)
```

ノードまたはリストとそのターゲットとのリンクを削除し（オブジェクトがすでにペアになっている場合）、`node`を返します。

オブジェクトが`PairedListNode`または`PairedLinkedList`の場合、リンクはオブジェクトとそのターゲットの両方から削除されます。

オブジェクトが`TargetedListNode`または`PairedLinkedList`の場合、リンクはオブジェクトからのみ削除されます。

関連情報として[`hastarget`](@ref)、[`addtarget!`](@ref)を参照してください。
