```
generate_next_level!(asg::AHSG{N,HCP}, tol::CT,maxlvl::Int) where {N,CT,CP<:AbstractCollocationPoint{N,CT},HCP<:AbstractHierarchicalCollocationPoint{N,CP}}
```

適応的に次の階層レベルのすべてのコレクションポイントを生成します。ここで、`norm(scaling_weight(cpt)) > tol && level(cpt)<maxlvl`です。

# コンストラクタ

  * `asg::AHSG{N,HCP}`: スパースグリッド
  * `tol::CT`: 許容誤差
  * `maxlvl::Int`: 最大階層レベル
