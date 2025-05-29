```
CoordinateVolume(DM::AbstractDataModel, Confnum::Real; N::Int=Int(1e5), WE::Bool=true, Approx::Bool=false, kwargs...) -> Real
```

レベル `Confnum` に関連する信頼領域の座標依存の見かけの体積をモンテカルロ積分を通じて計算します。特に評価が高価な尤度の場合、`Approx=true` を設定することで、多角形を用いて信頼領域を近似することにより、パフォーマンスを向上させることができます。
