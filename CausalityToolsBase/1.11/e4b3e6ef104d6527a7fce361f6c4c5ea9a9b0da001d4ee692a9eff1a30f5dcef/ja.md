```
get_minima_and_edgelengths(points, binning_scheme::RectangularBinning) -> (Vector{Float}, Vector{Float})
```

埋め込みの各軸に沿った最小値を見つけ、空間をグリッド化する方法を提供する矩形の `binning_scheme` に基づいて適切な `edge_lengths` を計算します。入力は点のベクトルであると仮定します。

`binning scheme` の詳細については [`RectangularBinning`](@ref) のドキュメントを参照してください。
