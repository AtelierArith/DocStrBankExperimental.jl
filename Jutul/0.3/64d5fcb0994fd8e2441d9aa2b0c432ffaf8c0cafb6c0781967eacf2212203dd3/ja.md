```
get_2d_interpolator(xs, ys, fs; method = BilinearInterpolant, cap_endpoints = true)
```

長さ `nx` の `xs` と長さ `ny` の `ys` に対して、`nx` x `ny` の行列として与えられた値の2D補間を生成します。デフォルトでは `cap_endpoints=true` であり、定数外挿が使用されます。外挿に対する細かい制御は、キーワード引数 `cap_x = (cap_low_x, cap_high_x)` を設定することで達成でき、`cap_y` に対しても同様です。
