```
verify_rounds(::Client, ::TestRound, ::Terse, rounds_as_graphs, pass_threshold)
```

クライアントのメタグラフのリストから複数の計算ラウンドを検証します。この関数はメタグラフを反復処理し、`ComputationRound`のラウンドタイプを持つものをスキップし、ラウンドを検証し、その結果をリストに格納します。関数は次に、失敗したラウンドの数をカウントします。失敗したラウンドの数が合格の閾値を超える場合、関数は`Abort()`を返し、そうでない場合は`Ok()`を返します。

# 引数

  * `::Client`: `Client`インスタンス。
  * `::TestRound`: `TestRound`インスタンス。
  * `::Terse`: `Terse`インスタンス。
  * `rounds_as_graphs`: クライアントのメタグラフのリスト。
  * `pass_threshold`: ラウンドが合格と見なされるための閾値。

# 戻り値

  * `Abort`または`Ok`: 失敗したラウンドの数が合格の閾値を超える場合は`Abort()`、そうでない場合は`Ok()`。

# 例

```julia
rounds_as_graphs = [create_meta_graph(Client()) for _ in 1:5]
pass_threshold = 3
round_verification = verify_rounds(Client(), TestRound(), Terse(), rounds_as_graphs, pass_threshold)
```
