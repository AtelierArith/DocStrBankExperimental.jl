```julia
struct DynPose2 <: DistributedFactorGraphs.InferenceVariable
```

速度成分を持つ動的ポーズ変数: `x, y, theta, dx/dt, dy/dt`

注意

  * 現在使用されている `SE2E2_Manifold` 定義は、Manifolds.jlへの移行を簡素化するためのハックです。#244を参照してください。
  * `SE2E2_Manifold` ハックを `ProductManifold(SpecialEuclidean(2), TranslationGroup(2))` に置き換えましたが、正しいか確認してください。
