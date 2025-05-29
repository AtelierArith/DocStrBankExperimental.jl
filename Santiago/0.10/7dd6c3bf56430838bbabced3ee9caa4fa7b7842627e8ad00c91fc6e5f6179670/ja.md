```julia
dot_file(sys::Santiago.System, file::AbstractString)
dot_file(
    sys::Santiago.System,
    file::AbstractString,
    no_group::Array{String}
)
dot_file(
    sys::Santiago.System,
    file::AbstractString,
    no_group::Array{String},
    options::String
)

```

`System`のDOTファイルを書き出します。生成されたファイルはGraphVizで視覚化できます。例: `dot -Tpng file.dot -o graph.png`

## 引数

  * `no_group`: プロットでグループ化されるべきでない機能グループの配列
  * `options`: *graphviz*オプションの文字列

```

```
