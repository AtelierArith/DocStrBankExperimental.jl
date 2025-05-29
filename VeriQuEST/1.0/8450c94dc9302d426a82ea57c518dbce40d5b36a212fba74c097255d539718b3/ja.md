```
clone_qureq(::Server,client_qureg,env)
```

サーバーのコンテキストで量子レジスタのクローンを作成します。

# 引数

  * `::Server`: この関数がサーバーのコンテキストで使用されることを示します。
  * `client_qureg`: クローンされる量子レジスタ。
  * `env`: 量子レジスタがクローンされるQuEST環境。

# 例

```julia
clone_qureq(Server(),client_qureg,env)
```
