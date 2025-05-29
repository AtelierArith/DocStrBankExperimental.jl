```
soft_assignment(conf_model::ConformalProbabilisticSet, fitresult, X; temp::Real=0.1)
```

この関数は、新しいデータ `X` に対してソフトアサインメント確率を計算するために使用できます [`soft_assignment(conf_model::ConformalProbabilisticSet; temp::Real=0.1)`](@ref)。フィッティングされたモデル $\mu$ (`fitresult`) と新しいサンプル `X` が提供されると、最初に新しいデータポイントの非適合スコアが計算されます。次に、既存の閾値/分位数 `q̂` を使用して最終的なソフトアサインメントが計算されます。
