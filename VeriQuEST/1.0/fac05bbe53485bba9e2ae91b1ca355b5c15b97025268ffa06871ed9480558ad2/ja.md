```
verify_round(::Client, ::TestRound, mg)
```

クライアントのメタグラフから計算のラウンドを検証します。この関数はメタグラフの頂点を反復処理し、頂点のタイプが `TrapQubit` であるかを確認し、頂点の隣接点とプロパティを取得し、検証結果を計算し、その結果をリストに格納します。すべての結果が `TrapPass` の場合、関数は 1 を返します（ラウンドが良好であることを示す）。そうでない場合は 0 を返します（ラウンドが不良であることを示す）。

# 引数

  * `::Client`: `Client` インスタンス。
  * `::TestRound`: `TestRound` インスタンス。
  * `mg`: クライアントのメタグラフ。

# 戻り値

  * `Int`: ラウンドが良好な場合は 1、ラウンドが不良な場合は 0。

# 例

```julia
mg = create_meta_graph(Client())
round_verification = verify_round(Client(), TestRound(), mg)
```
