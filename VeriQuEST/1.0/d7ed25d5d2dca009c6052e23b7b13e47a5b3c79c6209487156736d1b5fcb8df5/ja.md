```
verify_rounds(::Client, ::ComputationRound, ::Verbose, rounds_as_graphs)
```

クライアントのメタグラフのリストから複数の計算ラウンドを検証します。この関数は計算ラウンドの数をカウントし、計算ラウンドの出力を収集し、出力のモードを計算し、モードに一致する出力の数をカウントします。関数は、失敗したラウンドと合格したラウンドの数を含むタプルを返します。

# 引数

  * `::Client`: `Client` インスタンス。
  * `::ComputationRound`: `ComputationRound` インスタンス。
  * `::Verbose`: `Verbose` インスタンス。
  * `rounds_as_graphs`: クライアントのメタグラフのリスト。

# 戻り値

  * `Tuple`: 失敗したラウンドと合格したラウンドの数を含むタプル。

# 例

```julia
rounds_as_graphs = [create_meta_graph(Client()) for _ in 1:5]
round_verification = verify_rounds(Client(), ComputationRound(), Verbose(), rounds_as_graphs)
```
