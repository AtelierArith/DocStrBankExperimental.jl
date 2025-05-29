```
bdary_friction!(grid::VoronoiGrid, vDirichlet::Function, dt::Float64)
```

境界で粘性抵抗を適用します。これは、速度が表面の接線であるときの速度のディリクレ条件に使用されます。流入または流出には使用できません。関数 `vDirichlet` は単一の引数 `x::RealVector` を受け取り、境界の速度に対応する `RealVector` を返す必要があります。
