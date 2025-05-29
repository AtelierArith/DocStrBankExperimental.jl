```
dissipation_operator(D::PeriodicDerivativeOperator;
                     strength=one(eltype(D)),
                     order=accuracy_order(D),
                     mode=D.coefficients.mode)
```

`D`に適応された強さ`strength`で`order`-th導関数を近似する未分割差分を使用して、負半定値の`DissipationOperator`を作成します。導関数の評価は、`mode=ThreadedMode()`を選択することでスレッドを使用して並列化できます。
