```
getparentindex(idx, tree_type)
```

子ノード `idx` の親インデックスを取得します。

# 引数

  * `idx::T where T<:Integer`: 子ノードのインデックス。
  * `tree_type::Symbol`: ツリーの種類、すなわち `:binary` ツリーまたは `:quad` ツリー。

# 戻り値

  * `::T`: 親ノードのインデックス。
