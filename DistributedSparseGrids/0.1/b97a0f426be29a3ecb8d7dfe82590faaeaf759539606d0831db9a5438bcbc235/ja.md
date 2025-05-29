```
interpolate(asg::SG, x::VCT, stplvl::Int=numlevels(asg))
```

位置 `x` で補間します。

# 引数

  * `asg::SG<:AbstractHierarchicalSparseGrid{N,HCP}}`: 初期化された適応スパースグリッド
  * `cpts::Dict{SVector{N,Int},Dict{SVector{N,Int},HCP}}`: すべてのコレクションポイントを含む辞書
