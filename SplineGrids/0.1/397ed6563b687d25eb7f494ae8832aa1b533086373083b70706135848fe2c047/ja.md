```
SplineDimension(
    degree, 
    max_derivative_order, 
    knot_vector, 
    sample_points, 
    sample_indices, 
    eval, 
    eval_prev)
```

単一次元の基底関数のセットと、そのサンプリング方法を定義します。

## 引数

  * `degree`: 区分的多項式基底関数の次数。
  * `max_derivative_order`: 計算される基底関数の最大導関数の次数。
  * `knot_vector`: 基底関数が定義されるノットベクトル。
  * `sample_points`: 基底関数の定義域内でサンプリングされる点。ノットベクトルの境界内にある必要があります。
  * `sample_indices`: ノットベクトル内のサンプル点 `t` のインデックス `i` で、`knot_vector.knots[i] ≤ t < knot_vector.knots[i + 1]` を満たします。
  * `eval`: 形状 `(length(sample_points), degree + 1, max_derivative + 1)` の配列で、各サンプル点に対する基底関数の値を持ちます。
  * `eval_prev`: サンプル点が含まれる基底関数計算の中間結果のための補助配列で、要求された場合は導関数も含まれます。
