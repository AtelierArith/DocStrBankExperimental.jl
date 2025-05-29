```
var_coef_derivative_operator(source_of_coefficients, derivative_order, accuracy_order,
                             xmin, xmax, N, left_weights, right_weights, bfunc,
                             mode=FastMode())
```

`VarCoefDerivativeOperator`を作成し、`xmin`と`xmax`の間のグリッド上で、`N`個のグリッドポイントを使用して、変数係数`bfunc`を持つ`derivative_order`-th導関数を近似します。精度の順序は`accuracy_order`までで、係数は`source_of_coefficients`によって与えられます。導関数の評価は、`mode=ThreadedMode()`を選択することでスレッドを使用して並列化できます。
