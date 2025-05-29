```
LiFukushimaLineSearch(; lambda_0 = 1, beta = 1 // 2, sigma_1 = 1 // 1000,
    sigma_2 = 1 // 1000, eta = 1 // 10, nan_maxiters::Int = 5, maxiters::Int = 100)
```

非線形方程に対する導関数フリーのラインサーチとBroyden類似法のグローバル収束 [li2000derivative](@cite)。

!!! tip
    静的配列と数値の場合、`nan_maxiters` が `nothing` または `missing` のいずれかであれば、アルゴリズムの完全に非割り当ての実装を提供し、GPUカーネル内で使用できます。ただし、この特定のバージョンは `stats` と `reinit!` をサポートしておらず、それらは無視されます。さらに、検索の初期アルファを `1` に固定します。

