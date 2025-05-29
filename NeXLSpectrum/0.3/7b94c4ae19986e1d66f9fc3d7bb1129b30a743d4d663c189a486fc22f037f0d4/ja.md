```
roiimages(hss::HyperSpectrum, achs::AbstractVector{<:AbstractUnitRange{<:Integer}})
```

`achs`の各チャネル範囲における強度を表すグレイ画像の配列を作成します。これらは正規化されており、いずれかの画像の最も強いピクセルが白を定義します。（ピクセル間の:LiveTimeの違いを考慮します。）
