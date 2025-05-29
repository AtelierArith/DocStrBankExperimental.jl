```
SLIC(k, m; tol=1e-4, maxiter=10, weights=nothing)
```

ジオテーブルの行にラベルを割り当てるために、単純線形反復クラスタリング（SLIC）アルゴリズムを使用します。

このアルゴリズムは、地理的距離 `dₛ` と変数間の距離 `dᵥ` を組み合わせることによって、約 `k` クラスターを生成します。トレードオフは、加法モデル `dₜ = √(dᵥ² + m²(dₛ/s)²)` のハイパーパラメータ `m` によって制御され、ここで `s` はクラスター重心間の平均間隔です。

## オプション

  * `tol`     - k-meansアルゴリズムの許容誤差（デフォルトは `1e-4`）
  * `maxiter` - 最大反復回数（デフォルトは `10`）
  * `weights` - 各変数の重みを持つ辞書（デフォルトは `nothing`）

## 参考文献

  * Achanta et al. 2011. [SLIC superpixels compared to state-of-the-art superpixel methods](https://ieeexplore.ieee.org/document/6205760)

### 注意事項

変数（または特徴）は、パラメータ `m` の選択を容易にするために、コアアルゴリズムの前に `StdFeats` 変換で標準化されます。
