```
mutualinfo(a, b; normed=true) -> Float64
```

同じデータポイントの2つのクラスタリング間の*相互情報*を計算します。

`a`と`b`は、[`ClusteringResult`](@ref)インスタンスまたは割り当てベクトル（`AbstractVector{<:Integer}`）のいずれかです。

`normed`パラメータが`true`の場合、返される値は正規化された相互情報（対称的不確実性）です。詳細は「データマイニング実用機械ツールと技術」、Witten & Frank 2005を参照してください。

# 参考文献

> Vinh, Epps, and Bailey, (2009). *クラスタリング比較のための情報理論的尺度*. 第26回国際機械学習会議 - ICML ‘09の議事録。

