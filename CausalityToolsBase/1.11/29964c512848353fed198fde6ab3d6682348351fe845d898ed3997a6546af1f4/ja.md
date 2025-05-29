```
kerneldensity(pts, gridpts, kernel::BoxKernel; 
    h = silverman_rule(pts), 
    metric::Metric = Chebyshev(), 
    normalise = true)
```

ナイーブカーネル密度推定器 (Steuer et al., 2002)。

## 引数

  * **`pts`**: 密度を評価するための点。
  * **`gridpts`**: 密度を評価するためのグリッドポイントのセット。
  * **`kernel`**: `Kernel`タイプ。デフォルトは`BoxKernel`。`GaussianKernel`も使用可能。

## キーワード引数

  * **`h`**: バンド幅。ガウス密度を仮定して最適なバンド幅を計算するためにSilvermanのルールを使用します（注：ここではガウスカーネルを使用していないため、ずれている可能性があります）。
  * **`gridpts`**: 密度を評価するためのグリッドポイントのセット。
  * **`normalise`**: 密度を正規化して合計が1になるようにします。
  * **`metric`**: `Distances.jl`からの有効なメトリックのインスタンスで、非負、対称で三角不等式を満たす必要があります。デフォルトは`metric = Chebyshev()`。

## 戻り値

各グリッドポイントの密度推定。

## 参考文献

Steuer, R., Kurths, J., Daub, C.O., Weise, J. and Selbig, J., 2002. The mutual information:  detecting and evaluating dependencies between variables. Bioinformatics, 18(suppl_2), pp.S231-S240.
