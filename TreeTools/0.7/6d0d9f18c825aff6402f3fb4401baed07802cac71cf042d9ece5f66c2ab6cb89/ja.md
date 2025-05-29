```
graft!(tree::Tree, n, r; graft_on_leaf=false, time=branch_length(n))
```

`n`を`r`に接ぎ木し、接ぎ木されたノードを返します。`r`はラベルまたは`TreeNode`であり、`tree`に属している必要があります。`n`は`TreeNode`または`Tree`であることができます。後者の場合、`n`は接ぎ木される前に*コピー*されます。`n`の部分木のノードは、`tree`に属してはいけません。

`r`が葉であり、`graft_on_leaf`が`false`（デフォルト）に設定されている場合、エラーが発生します。
