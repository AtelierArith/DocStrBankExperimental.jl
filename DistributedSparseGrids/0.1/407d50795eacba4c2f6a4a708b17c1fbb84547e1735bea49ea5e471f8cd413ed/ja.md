```
init_weights_inplace_ops!(asg::SG, cpts::AbstractVector{HCP}, fun::F)
```

`cpts`内のすべての重みをインプレース操作で（再）計算します。インプレース関数`mul!(::RT,::RT)`,`mul!(::RT,::Float64)`,`add!(::RT,::RT)`を定義する必要があります。

# 引数

  * `asg::SG<:AbstractHierarchicalSparseGrid{N,HCP}}`: 適応型スパースグリッド
  * `cpts::AbstractVector{HCP}`: `cpts`内のコレクションポイントのすべての重みが（再）計算されます。
  * `fun`::補間される関数。
