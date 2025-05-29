```
ladderize_tree(root::T, ascending::Bool=true)::T where T<:AbstractNode
```

この関数は、ツリーの階段状のコピーを返します。すなわち、すべてのレベルのノードがその子孫の数でソートされたコピーです。

  * `root` : ツリーのルートノード。
  * `ascending` : ブール値で、昇順（true）または降順（false）でソートするかどうかを決定します。
