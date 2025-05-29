```
remove_from_tree!(tree_tokens::Vector{String}, taxa_to_remove::Union{Array{String,1},Bool})
```

Newick形式の木から特定の分類群を削除します。

# 引数

  * `tree_tokens::Vector{String}`: Newick形式の木、トークン化されたもの。
  * `taxa_to_remove::Union{Array{String,1},Bool}`: 削除される分類群。
