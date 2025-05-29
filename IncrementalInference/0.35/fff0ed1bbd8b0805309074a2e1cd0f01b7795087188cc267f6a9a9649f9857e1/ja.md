```julia
mutable struct SolverParams <: DistributedFactorGraphs.AbstractParams
```

DistributedFactoGraphのためのソルバーパラメータ。

開発ノート

  * FIXME Parameters.jlからkwargsを使用するように変更
  * TODO NothingUnionを削除
  * TODO 一般的な@kwargs構造体アプローチにアップグレード
