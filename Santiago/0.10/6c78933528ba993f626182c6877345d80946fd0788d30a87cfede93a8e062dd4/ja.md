```julia
dot_string(sys::Santiago.System) -> String
dot_string(
    sys::Santiago.System,
    no_group::Array{String}
) -> String
dot_string(
    sys::Santiago.System,
    no_group::Array{String},
    options::String
) -> String

```

`System`をGraphVizのdot形式で表す`String`を返します。

## 引数

  * `no_group`: プロットでグループ化されるべきでない機能グループの配列
  * `options`: *graphviz*オプションの文字列

```

```
