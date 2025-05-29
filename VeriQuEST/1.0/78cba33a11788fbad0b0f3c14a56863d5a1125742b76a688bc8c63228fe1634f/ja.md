```
create_resource(server::NoisyServer, client_graph, client_qureg)
```

`NoisyServer`のリソースを作成します。クライアントのグラフと量子レジスタをクローンし、サーバーの量子レジスタにノイズを追加し、サーバーのグラフをエンタングルします。サーバーの量子環境、量子状態、およびグラフを含む辞書を返します。

# 引数

  * `server::NoisyServer`: リソースが作成される`NoisyServer`インスタンス。
  * `client_graph`: クローンされるクライアントのグラフ。
  * `client_qureg`: クローンされるクライアントの量子レジスタ。

# 戻り値

  * `Dict`: サーバーの量子環境（`"env"`）、量子状態（`"quantum_state"`）、およびグラフ（`"graph"`）を含む辞書。

# 例

```julia
server = NoisyServer(noise_model)
client_graph = create_graph(Client(), 3)
client_qureg = QuantumRegister(3)
resource = create_resource(server, client_graph, client_qureg)
```
