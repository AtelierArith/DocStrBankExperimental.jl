```
EmpiricalTransiogram(data, var; [options])
```

カテゴリ変数 `var` が地理空間データ `data` に格納されている場合の経験的（すなわち実験的）全方向トランジオグラムを計算します。

## オプション

  * nlags     - ラグの数（デフォルトは `20`）
  * maxlag    - 長さ単位での最大ラグ（デフォルトはバウンディングボックスの最小辺の1/2）
  * distance  - カスタム距離関数（デフォルトは `Euclidean` 距離）
  * algorithm - 蓄積アルゴリズム（デフォルトは `:ball`）

利用可能なアルゴリズム：

  * `:full` - データ内のすべての点のペアをループ
  * `:ball` - 最大ラグボール内のすべての点をループ

すべての実装されたアルゴリズムは同じ結果を生成します。最大ラグがデータの領域のバウンディングボックスよりもかなり小さい場合、`:ball` アルゴリズムはかなり高速です。

参照： [`DirectionalTransiogram`](@ref), [`PlanarTransiogram`](@ref), [`EmpiricalTransiogramSurface`](@ref)。

## 参考文献

  * Carle, S.F. & Fogg, G.E. 1996. [Transition probability-based indicator geostatistics](https://link.springer.com/article/10.1007/BF02083656)
  * Carle et al 1998. [Conditional Simulation of Hydrofacies Architecture: A Transition Probability/Markov Approach](https://doi.org/10.2110/sepmcheg.01.147)

```
