```
reinit!(cv::CellValues, cell::AbstractCell, x::AbstractVector)
reinit!(cv::CellValues, x::AbstractVector)
reinit!(fv::FacetValues, cell::AbstractCell, x::AbstractVector, facet::Int)
reinit!(fv::FacetValues, x::AbstractVector, function_gradient::Int)
```

セル座標 `x` を持つセルまたはファセットの `CellValues`/`FacetValues` オブジェクトを更新します。形状関数の導関数と新しい積分重みが計算されます。非単位マッピングを持つ補間の場合、現在の `cell` も必要です。
