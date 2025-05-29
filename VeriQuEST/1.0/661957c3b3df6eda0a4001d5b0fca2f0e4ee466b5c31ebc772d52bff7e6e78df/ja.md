```
verify_rounds(::Client, ::ComputationRound, ::Terse, rounds_as_graphs)
```

クライアントのメタグラフのリストから複数の計算ラウンドを検証します。この関数は計算ラウンドの数をカウントし、計算ラウンドの出力を収集し、出力のモードを計算し、モードに一致する出力の数をカウントします。モードに一致する出力の数が計算ラウンドの半分を超える場合、関数は `Ok()` を返し、そうでない場合は `Abort()` を返します。

# 引数

  * `::Client`: `Client` インスタンス。
  * `::ComputationRound`: `ComputationRound` インスタンス。
  * `::Terse`: `Terse` インスタンス。
  * `rounds_as_graphs`: クライアントのメタグラフのリスト。

# 戻り値

  * `Ok` または `Abort`: モードに一致する出力の数が計算ラウンドの半分を超える場合は `Ok()`、そうでない場合は `Abort()`。

# 例

```julia
rounds_as_graphs = [create_meta_graph(Client()) for _ in 1:5]
round_verification = verify_rounds(Client(), ComputationRound(), Terse(), rounds_as_graphs)
```
