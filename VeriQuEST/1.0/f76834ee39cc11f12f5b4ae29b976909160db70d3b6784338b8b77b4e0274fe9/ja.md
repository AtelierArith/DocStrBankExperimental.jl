```
clone_graph(::Server,client_graph)
```

サーバーのコンテキストでグラフのクローンを作成します。

# 引数

  * `::Server`: この関数がサーバーのコンテキストで使用されることを示します。
  * `client_graph`: クローンされるグラフ。

# 例

```julia
clone_graph(Server(),client_graph)
```
