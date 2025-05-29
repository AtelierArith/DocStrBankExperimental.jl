```
dissipation_operator([source_of_coefficients=MattssonSvärdNordström2004()],
                     D::DerivativeOperator{T};
                     strength=one(T),
                     order::Int=accuracy_order(D),
                     mode=D.coefficients.mode)
```

重み付きの `order`-階微分を近似する未分割差分を使用して、導関数演算子 `D` に適応した負半定値の `DissipationOperator` を作成します。導関数の評価は、`mode=ThreadedMode()` を選択することでスレッドを使用して並列化できます。
