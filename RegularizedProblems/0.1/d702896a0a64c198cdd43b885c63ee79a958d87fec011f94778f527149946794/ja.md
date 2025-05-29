```
rmodel = RegularizedNLPModel(model, regularizer)
rmodel = RegularizedNLSModel(model, regularizer)
```

正則化最適化モデルを表す集約型、すなわち次の形のモデル

```
minimize f(x) + h(x),
```

ここで、fは滑らかで（通常はリプシッツ連続勾配を持つと仮定される）、hは下半連続（おそらく近接制約を持つ必要がある）。

正則化モデルは以下で構成される

  * `model <: AbstractNLPModel`: モデルの滑らかな部分、例えば `FirstOrderModel`
  * `h`: モデルの非滑らかな部分; 通常は `ProximalOperators.jl` で定義された正則化子
  * `selected`: 正則化子hを適用すべき変数のサブセット（デフォルト: すべて）。

この集約型は、モデルを表す単一のオブジェクトでソルバーを呼び出すために使用できますが、特にSolverBenchmark.jlでの使用に便利で、問題が単一のオブジェクトで定義されることを期待しています。
