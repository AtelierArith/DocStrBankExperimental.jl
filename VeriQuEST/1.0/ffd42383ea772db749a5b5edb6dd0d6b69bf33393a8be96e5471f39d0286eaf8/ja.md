```
create_resource(::Server,client_graph,client_qureg)
```

サーバーのコンテキストでリソースを作成します。

# 引数

  * `::Server`: この関数がサーバーのコンテキストで使用されることを示します。
  * `client_graph`: コピー/クローンされるグラフ。
  * `client_qureg`: コピー/クローンされる量子レジスタ。

# 例

```julia
create_resource(Server(),client_graph,client_qureg)
```
