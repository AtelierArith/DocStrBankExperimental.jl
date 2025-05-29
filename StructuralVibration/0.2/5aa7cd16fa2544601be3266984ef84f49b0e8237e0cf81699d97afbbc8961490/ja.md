```
DirectFreqProblem(K, M, C, F, freq, So)
```

直接ソルバーにデータを供給してモーダル周波数を計算するための構造体

**フィールド**

  * `K::AbstractMatrix`: 剛性行列
  * `M::AbstractMatrix`: 質量行列
  * `C::AbstractMatrix`: 減衰行列
  * `F::AbstractMatrix`: 力行列
  * `freq::AbstractRange`: 興味のある周波数
  * `So::AbstractMatrix`: 観測点の選択行列
