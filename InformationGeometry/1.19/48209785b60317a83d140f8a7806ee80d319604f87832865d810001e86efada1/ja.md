```
ConfidenceRegionVolume(DM::AbstractDataModel, Confnum::Real; N::Int=Int(1e5), WE::Bool=true, Approx::Bool=false, kwargs...) -> Real
```

レベル `Confnum` に関連する信頼領域の座標不変体積を、幾何学的密度因子を統合することによってモンテカルロ法で計算します。評価が特に高価な尤度の場合、`Approx=true` を設定することで、多角形を用いて信頼領域を近似することにより、パフォーマンスを向上させることができます。
