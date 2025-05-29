## `score` (SpatiallyWeighted)

```julia
score(vol::AbstractMatrix, calibration, alg::SpatiallyWeighted)

score(vol::AbstractMatrix, μ, σ, alg::SpatiallyWeighted)

score(vol::AbstractArray, calibration, alg::SpatiallyWeighted)

score(vol::AbstractArray, μ, σ, alg::SpatiallyWeighted)
```

Spatially Weighted Calcium Scoringアルゴリズムを使用してカルシウムスコアを計算します。この方法は、[MESA研究](https://doi.org/10.1186/1471-2342-12-14)に概説されているように、以前のキャリブレーション（通常は100 mg/cc）に基づいて各ボクセルに重みを付けることによってしきい値処理を回避します。

関数は異なるパラメータで呼び出すことができます：

1. `vol::AbstractMatrix`, `calibration`, `alg::SpatiallyWeighted` - キャリブレーション配列を持つ2Dボリュームにアルゴリズムを適用します。
2. `vol::AbstractMatrix`, `μ`, `σ`, `alg::SpatiallyWeighted` - 与えられた平均`μ`と標準偏差`σ`を持つ2Dボリュームにアルゴリズムを適用します。
3. `vol::AbstractArray`, `calibration`, `alg::SpatiallyWeighted` - キャリブレーション配列を持つ3Dボリュームにアルゴリズムを適用します。
4. `vol::AbstractArray`, `μ`, `σ`, `alg::SpatiallyWeighted` - 与えられた平均`μ`と標準偏差`σ`を持つ3Dボリュームにアルゴリズムを適用します。

#### 入力

  * `vol`: 興味のある領域のみを含む入力ボリューム。これは2D（`AbstractMatrix`）または3D（`AbstractArray`）ボリュームです。
  * `calibration`: 各ボクセルに重みを付けるための以前のキャリブレーション。
  * `μ`, `σ`: 与えられた平均と標準偏差。
  * `alg::SpatiallyWeighted`: 空間的に重み付けされたスコアリングアルゴリズム`SpatiallyWeighted()`。

#### 戻り値

  * `sw_score`: 既存の冠動脈カルシウムスコアリング方法と比較して、動脈硬化の連続的で改善された測定を提供する総合的な空間的重み付けスコア。

#### 参考文献

[冠動脈石灰化を定量化するための代替方法：動脈硬化の多民族研究（MESA）](https://doi.org/10.1186/1471-2342-12-14)

[多民族動脈硬化研究における空間的に重み付けされた冠動脈カルシウムスコアと冠動脈心疾患イベント](https://doi.org/10.1161/CIRCIMAGING.120.011981)
