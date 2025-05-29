```
rm_lineinfo(ex)
```

与えられた式から `LineNumberNode` を削除します。

!!! tips
    マクロ呼び出し内の `LineNumberNode` は削除されません。なぜなら、`macrocall` 式は `LineNumberNode` を必要とするからです。詳細は [issues/#9](https://github.com/Roger-luo/Expronicon.jl/issues/9) を参照してください。

