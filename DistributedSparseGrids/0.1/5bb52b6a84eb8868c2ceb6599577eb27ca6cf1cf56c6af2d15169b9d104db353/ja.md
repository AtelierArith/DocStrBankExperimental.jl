```
integrate(asg::SG) where {N,CP,RT,HCP<:AbstractHierarchicalCollocationPoint{N,CP,RT}, SG<:AbstractHierarchicalSparseGrid{N,HCP}}
```

スパースグリッドを統合します。RTのインスタンスを返します。

# コンストラクタ

  * `asg::SG`: 適応スパースグリッド
