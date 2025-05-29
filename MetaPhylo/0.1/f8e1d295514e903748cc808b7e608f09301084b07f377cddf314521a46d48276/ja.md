```
swapchildren!(tree::Tree, idx::Integer, newchildren)
```

指定された `idx` ノードの子インデックスを与えられた `newchildren` に入れ替えます。子要素と `newchildren` の要素は一致している必要があります。入れ替えに失敗した場合は `false` を返し、それ以外の場合は `true` を返します。
