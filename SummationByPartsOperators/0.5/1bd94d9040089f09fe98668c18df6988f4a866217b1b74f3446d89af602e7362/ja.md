```
derivative_operator(source_of_coefficients,
                    derivative_order, accuracy_order,
                    xmin, xmax, N, mode=FastMode())
derivative_operator(source_of_coefficients;
                    derivative_order, accuracy_order,
                    xmin, xmax, N, mode=FastMode())
```

[`DerivativeOperator`](@ref) を作成して、`xmin` と `xmax` の間のグリッド上で `N` グリッドポイントを使用して `derivative_order`-階の導関数を、`accuracy_order` の精度まで近似します。係数は `source_of_coefficients` によって与えられます。導関数の評価は、`mode=ThreadedMode()` を選択することでスレッドを使用して並列化できます。
