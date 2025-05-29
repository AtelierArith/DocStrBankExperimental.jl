```
linear_dominated_bounder(fT::TaylorModel1, ϵ=1e-3::Float64, max_iter=5::Int)
```

テイラーモデル `fT` のためのより厳密な多項式境界を線形支配境界アルゴリズムによって計算します。線形支配アルゴリズムは、`fT` の境界が `ϵ` より厳密になるか、ステップ数が `max_iter` に達するまで適用されます。返される境界は、`TaylorModel1` の余剰を含む改善された多項式境界に対応します。
