```julia
struct GenericTensorNetwork{CFG, CT, LT}
```

```
GenericTensorNetwork(problem::ConstraintSatisfactionProblem; openvertices=(), fixedvertices=Dict(), optimizer=GreedyMethod())
```

[`ConstraintSatisfactionProblem`](@ref) から生成された一般的なテンソルネットワークです。

## 位置引数

  * `problem` はグラフ問題です。
  * `code` はテンソルネットワーク収束コードです。
  * `fixedvertices` は固定次元を指定する辞書です。
