```
insert_node!(mother::T, children::Vector{T})::T where T<:AbstractNode
```

この関数は、母ノードの後にノードをツリーに挿入し、母の子供のサブセットをその子供として取得します。

挿入されたノードを返します。

  * `mother` : 新しく挿入されたノードを追加するノード。
  * `children` : "mother" で参照されるノードの子供を、新しく挿入されたノードの子供として再割り当てする。
