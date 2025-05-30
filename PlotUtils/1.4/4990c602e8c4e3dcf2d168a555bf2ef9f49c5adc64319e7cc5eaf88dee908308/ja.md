```
adapted_grid(f, minmax::Tuple{Number, Number}; max_recursions = 7, max_curvature = 0.01, n_points = 31)
```

関数 `f` の区間 [minmax[1], minmax[2]] 上にグリッド `x` を計算し、`plot(f, x)` が滑らかで「良い」プロットを生成するようにします。使用される方法は、最初に `n_points` の均一なグリッドを作成し、二次導関数が大きいと近似される区間を細分化することです。区間が「十分に直線的」になると、それ以上は分割されません。関数は区間の端点で評価されます。

パラメータ `max_recursions` は、各区間がどれだけ細分化されることが許可されるかを計算し、`max_curvature` は、曲率がこの値未満の場合、区間がこれ以上細分化される必要がないことを指定します。
