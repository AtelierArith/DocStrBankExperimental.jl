```
l = DoublyLinkedList{::Type}()
l = DoublyLinkedList(elts...)
```

指定された型のデータを含むノードを持つ[`ListNode`](@ref)で構成された`DoublyLinkedList`を作成します。

リストには、その長さ`len`、リストの先頭にある「ダミー」ノード`head`、およびリストの末尾にある「ダミー」ノード`tail`が含まれています。

リスト`l`の最初の「実際の」ノードには`l.head.next`または`head(l)`でアクセスできます。同様に、最後の「実際の」ノードには`l.tail.prev`または`tail(l)`でアクセスできます。

[`ListNode`](@ref)、[`SkipList`](@ref)、[`PairedLinkedList`](@ref)、[`TargetedLinkedList`](@ref)も参照してください。
