```
ladderize_tree!(root::T, ascending::Bool=true) where T<:AbstractNode
```

この関数は木をインプレースでラダライズします。つまり、すべてのレベルのノードをその子孫の数でソートします。

  * `root` : 木のルートノード。
  * `ascending` : ブール値で、昇順（true）または降順（false）でソートするかを決定します。
