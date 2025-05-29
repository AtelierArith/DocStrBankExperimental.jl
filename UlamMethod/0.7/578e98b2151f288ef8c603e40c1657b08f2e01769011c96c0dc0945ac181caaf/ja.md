```
abstract type ReinjectionAlgorithm
```

内側に向かうニルヴァーナからの軌道を再分配する方法を制御するアルゴリズムの抽象型です。

各サブタイプ `reinj_algo` は以下を実装する必要があります：

  * 関数 `reinject!(binner, Pij, reinj_algo)` は、ビニングアルゴリズム `binner` に基づいて、遷移行列 `Pij` をその場で修正します。この関数は、元の `Pij` の最大の強連結成分が取得された後、行確率化される前に適用されます。
