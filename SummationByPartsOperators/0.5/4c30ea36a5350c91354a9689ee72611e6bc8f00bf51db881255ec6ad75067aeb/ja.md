```
periodic_derivative_operator(derivative_order, accuracy_order, grid,
                             left_offset=-(accuracy_order+1)÷2, mode=FastMode())
```

`derivative_order`-階の導関数を、`left_offset`によって決定される最も左のグリッドポイントを使用して、精度の順序`accuracy_order`まで均一な`grid`上で近似する`PeriodicDerivativeOperator`を作成します。導関数の評価は、`mode=ThreadedMode())`を選択することでスレッドを使用して並列化できます。
