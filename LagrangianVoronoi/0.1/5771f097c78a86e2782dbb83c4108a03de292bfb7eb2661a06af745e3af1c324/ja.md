```
MultiphaseSolver(grid::VoronoiGrid, quality_threshold::Float64 = 0.25)
```

マルチフェーズ投影ステップのソルバーを構築します。キーワード引数 `quality_threshold` は、セルの品質が不十分なために `dv` を投影しないべき時期を決定します。これらの問題のあるケースでは、シミュレーションの安定性が物理的な精度よりも優先されます。
