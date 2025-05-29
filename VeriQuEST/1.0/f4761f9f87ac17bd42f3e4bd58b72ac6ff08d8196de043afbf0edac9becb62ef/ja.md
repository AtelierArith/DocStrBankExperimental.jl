```
entangle_graph!(::Server,qureg,graph)
```

サーバーのコンテキストでグラフと量子レジスタをエンタングルします。

# 引数

  * `::Server`: この関数がサーバーのコンテキストで使用されることを示します。
  * `qureg`: エンタングルされる量子レジスタ。
  * `graph`: 量子レジスタがエンタングルされるグラフ。

# 例

```julia
entangle_graph!(Server(),qureg,graph)
```
