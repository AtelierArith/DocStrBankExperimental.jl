```
variation_test(depth::Int, altdepth::Int, quality::Float64)
```

与えられた平均ベースコール `quality` に基づいて、合計 `depth` と変異深度 `altdepth` を持つ変異が発生する可能性を判断するために、フィッシャーの正確検定を実施します。テストの $p$-値を返します。
