```
circulant_similarity(simfun::AbstractSimilarity, x, y, W::Int)
```

循環行列を循環スパースデータで返します。各非ゼロ `S[i,j,b]` は、`x` と `y` の線形化されたピクセル位置で評価された `simfun` によって populated されます。すなわち、`S[i,j,b] = simfun(x[...,i,b], y[...,j,b], W)` であり、max(i⃗, j⃗) ≤ W です。非ゼロエントリの位置は、ウィンドウサイズ `W` と `x` および `y` の空間次元の数によって決定されます。

他にも [`DotSimilarity`](@ref)、[`DistanceSimilarity`](@ref) を参照してください。
