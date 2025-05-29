```
write_newick(io::IO, tree::Tree; kwargs...)
write_newick(filename::AbstractString, tree::Tree, mode="w"; kwargs...)
write_newick(tree::Tree; kwargs...)
```

`tree`に対応するNewick文字列を`io`または`filename`に書き込みます。出力が提供されていない場合、Newick文字列を返します。`internal_labels == false`の場合、文字列に内部ノードのラベルを書き込みません。
