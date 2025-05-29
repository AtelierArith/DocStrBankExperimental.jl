```
periodic_central_derivative_operator(derivative_order, accuracy_order,
                                     xmin, xmax, N, mode=FastMode())
```

[`PeriodicDerivativeOperator`](@ref)を作成して、`xmin`と`xmax`の間の均一グリッド上で`N`グリッドポイントを使用して`derivative_order`-次の導関数を精度順序`accuracy_order`まで近似します。導関数の評価は、`mode=ThreadedMode()`を選択することでスレッドを使用して並列化できます。
