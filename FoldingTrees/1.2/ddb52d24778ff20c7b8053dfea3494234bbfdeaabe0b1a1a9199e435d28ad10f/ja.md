```
newnode, newdepth = next(node, depth::Int=0)
```

深さ優先探索で次のノードを返します。`depth`はルートの下にあるレベルの数をカウントします。親は子ノードの前に訪問されます。
