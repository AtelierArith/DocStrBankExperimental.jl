```
l = TargetLinkedList{T,R}()
l = TargetLinkedList{T,R}(elts...)
l = TargetLinkedList(list)
```

指定された型のデータを含む[`TargetedListNode`](@ref)で構成された`TargetLinkedList`を作成します。各ノードは、リストの`target`に属するノードへの相互リストリンクを持つことができます。

リストには、その長さ`len`、リストの先頭にある「ダミー」ノード`head`、リストの末尾にある「ダミー」ノード`tail`が含まれています。また、リストはその「ターゲット」リストへの参照も含んでいます。

リスト`l`の最初の「実際の」ノードには`l.head.next`または`head(l)`でアクセスできます。同様に、最後の「実際の」ノードには`l.tail.prev`または`tail(l)`でアクセスできます。

[`TargetedListNode`](@ref)、[`DoublyLinkedList`](@ref)、[`PairedLinkedList`](@ref)も参照してください。
