```
parse_tree(file_path::String; taxa_to_remove::Union{Array{String,1},Bool}=false)
```

Nexusファイルを受け取り、木の内部表現（およびその他の関連情報）を返します。

# 引数

  * `file_path::String`: Nexusファイルへのファイルパス。
  * `taxa_to_remove::Union{Array{String,1},Bool}=false`: 削除されるタクサ（該当する場合）。
