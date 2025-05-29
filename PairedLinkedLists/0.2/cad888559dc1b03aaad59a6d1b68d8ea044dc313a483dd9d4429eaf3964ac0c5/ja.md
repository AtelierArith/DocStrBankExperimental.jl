```
addtarget!(node, target_node)
addtarget!(list, target_list)
```

提供されたノードまたはリストと同じタイプの別のオブジェクトとの間にリンクを追加し、その`target`を割り当てます。

最初のオブジェクトが`PairedListNode`または`PairedLinkedList`であり、いずれかのオブジェクトが以前にターゲットを持っていた場合、以前のリンクは削除されます。

最初のオブジェクトが`TargetedListNode`または`TargetedLinkedList`の場合、2番目のオブジェクトは変更されません。

参照：[`hastarget`](@ref)、[`removetarget!`](@ref)
