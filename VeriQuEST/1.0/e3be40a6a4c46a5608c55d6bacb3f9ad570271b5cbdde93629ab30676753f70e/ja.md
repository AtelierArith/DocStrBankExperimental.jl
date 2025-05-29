```
create_resource(::MaliciousServer, client_graph, client_qureg, malicious_angles::Union{Float64,Vector{Float64}})
```

悪意のあるサーバーのためのリソース辞書を作成します。これには、クローンされたグラフ、量子環境、量子レジスタ、および一連の悪意のある角度が含まれます。

# 引数

  * `::MaliciousServer`: この関数が悪意のあるサーバーの文脈で使用されることを示します。
  * `client_graph::Graph`: クローンされるクライアントのグラフ。
  * `client_qureg::QuEST object`: クローンされるクライアントの量子レジスタ。
  * `malicious_angles::Union{Float64,Vector{Float64}}`: 悪意のある行動に使用される角度。

# 例

```julia
client_graph = create_graph(Client(), 3)
client_qureg = create_qureg(Client(), 3)
malicious_angles = [π/4, π/2, 3π/4]
create_resource(MaliciousServer(), client_graph, client_qureg, malicious_angles)
```
