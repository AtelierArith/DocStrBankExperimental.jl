```
parent_branch(tree::AbstractPhyloTree, idx::Integer)
```

指定された `idx` ノードとその親ノードの間のブランチ（エッジ）を返します。ノードがルートの場合、これは `nothing` を返します。
