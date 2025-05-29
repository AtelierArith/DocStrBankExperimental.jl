```
l = PairedLinkedList{::Type}()
l = PairedLinkedList{::Type}(elts...)
```

指定された型のデータを含む[`PairListNode`](@ref)で構成された`PairedLinkedList`を作成します。各ノードは、リストの`target`に属するノードへのリスト間リンクを持つことができます。

リストには、その長さ`len`、リストの先頭にある「ダミー」ノード`head`、およびリストの末尾にある「ダミー」ノード`tail`が含まれています。

リスト`l`の最初の「実際の」ノードには`l.head.next`または`head(l)`でアクセスできます。同様に、最後の「実際の」ノードには`l.tail.prev`または`tail(l)`でアクセスできます。

他にも[`PairedListNode`](@ref)、[`PairedSkipList`](@ref)、[`DoublyLinkedList`](@ref)、[`TargetedLinkedList`](@ref)を参照してください。
