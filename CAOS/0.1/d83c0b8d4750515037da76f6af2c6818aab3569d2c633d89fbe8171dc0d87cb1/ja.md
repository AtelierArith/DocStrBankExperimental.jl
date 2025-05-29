```
get_nodes(tree::String ; taxa_to_remove::Union{Array{String,1},Bool}=false)
```

Newick形式の木を受け取り、木の内部表現を返します。

# 引数

  * `tree::String`: Newick形式の木。
  * `taxa_to_remove::Union{Array{String,1},Bool}=false`: 削除されるタクサ（該当する場合）。
