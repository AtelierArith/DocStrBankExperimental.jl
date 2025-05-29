```
EmpiricalVariogram(data, var₁, var₂=var₁; [options])
```

変数 `var₁` と `var₂` が地理空間データ `data` に格納されている場合の経験的（すなわち実験的）全方向（交差）変動関数を計算します。

## オプション

  * nlags     - ラグの数（デフォルトは `20`）
  * maxlag    - 長さ単位での最大ラグ（デフォルトはバウンディングボックスの最小辺の1/2）
  * distance  - カスタム距離関数（デフォルトはユークリッド距離）
  * estimator - 変動関数推定器（デフォルトは `:matheron` 推定器）
  * algorithm - 蓄積アルゴリズム（デフォルトは `:ball`）

利用可能な推定器：

  * `:matheron` - 二乗差に基づく単純な推定器
  * `:cressie`  - 差の4乗に基づくロバストな推定器

利用可能なアルゴリズム：

  * `:full` - データ内のすべての点のペアをループ
  * `:ball` - 最大ラグボール内のすべての点をループ

すべての実装されたアルゴリズムは同じ結果を生成します。最大ラグがデータの領域のバウンディングボックスよりもかなり小さい場合、`:ball` アルゴリズムはかなり高速です。

参照： [`DirectionalVariogram`](@ref), [`PlanarVariogram`](@ref), [`EmpiricalVariogramSurface`](@ref).

## 参考文献

  * Chilès, JP and Delfiner, P. 2012. [Geostatistics: Modeling Spatial Uncertainty](https://onlinelibrary.wiley.com/doi/book/10.1002/9781118136188)
  * Webster, R and Oliver, MA. 2007. [Geostatistics for Environmental Scientists](https://onlinelibrary.wiley.com/doi/book/10.1002/9780470517277)
  * Hoffimann, J and Zadrozny, B. 2019. [Efficient variography with partition variograms](https://www.sciencedirect.com/science/article/pii/S0098300419302936)

```
