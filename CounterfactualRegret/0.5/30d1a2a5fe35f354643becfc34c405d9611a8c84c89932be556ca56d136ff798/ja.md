```
OSCFRSolver(game; method=Vanilla(), baseline=ZeroBaseline(), ϵ::Float64 = 0.6)
```

いくつかの `game` で結果サンプリングCFRソルバーをインスタンス化します。

単一のツリー探索のためにすべてのプレイヤーから単一のアクションをサンプリングします。探索を完了するのにかかる時間は O(d) で、ここで d はゲームの深さです。

`ϵ` - 探索パラメータ

利用可能なベースライン:

  * [`ZeroBaseline`](@ref) - ベースラインなしと同等
  * [`ExpectedValueBaseline`](@ref)
