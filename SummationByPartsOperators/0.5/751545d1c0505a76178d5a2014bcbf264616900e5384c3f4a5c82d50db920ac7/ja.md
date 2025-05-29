```
dissipation_operator(source_of_coefficients, order, xmin, xmax, N,
                     left_weights, right_weights, mode=FastMode())
```

重み付きの `order`-th 微分を近似するための未分割差分を使用して、`xmin` と `xmax` の間のグリッド上に負半定義の `DissipationOperator` を作成します。グリッドポイントは `N` で、精度の順序は 2 までで、係数は `source_of_coefficients` によって与えられます。ノルム行列は `left_weights` と `right_weights` によって与えられます。微分の評価は、`mode=ThreadedMode()` を選択することでスレッドを使用して並列化できます。
