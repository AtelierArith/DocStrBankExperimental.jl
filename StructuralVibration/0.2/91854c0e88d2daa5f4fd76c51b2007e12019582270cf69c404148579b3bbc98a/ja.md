```
DirectFRFProblem(K, M, C, freq, So, Se)
```

直接ソルバーにデータを供給する構造体で、FRFを計算します

**フィールド**

  * `K::AbstractMatrix`: 剛性行列
  * `M::AbstractMatrix`: 質量行列
  * `C::AbstractMatrix`: 減衰行列
  * `freq::AbtractRange`: 興味のある周波数
  * `So::AbstractMatrix`: 観測点の選択行列
  * `Se::AbstractMatrix`: 励起点の選択行列
