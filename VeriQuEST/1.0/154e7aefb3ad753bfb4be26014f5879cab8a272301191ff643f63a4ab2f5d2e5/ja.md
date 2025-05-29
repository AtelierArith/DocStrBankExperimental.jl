```
get_mode_output(::Client, ::ComputationRound, rounds_as_graphs::Vector)
```

クライアントのメタグラフのリストから計算ラウンドの出力を収集し、出力のモードを返します。この関数はメタグラフを反復処理し、`TestRound`のラウンドタイプを持つものをスキップし、計算ラウンドの出力を取得してリストに格納します。その後、出力のモードを計算して返します。

# 引数

  * `::Client`: `Client`インスタンス。
  * `::ComputationRound`: `ComputationRound`インスタンス。
  * `rounds_as_graphs::Vector`: クライアントのメタグラフのリスト。

# 戻り値

  * `mode(outputs)`: 出力のモード。

# 例

```julia
rounds_as_graphs = [create_meta_graph(Client()) for _ in 1:5]
mode_output = get_mode_output(Client(), ComputationRound(), rounds_as_graphs)
```
