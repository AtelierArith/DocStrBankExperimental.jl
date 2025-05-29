```
weight = project(trace::U, selection::Selection)
```

選択された選択肢がトレースで持つ値を取る確率を推定します。

トレース $(x, r, t)$ (`trace`) とアドレスの集合 $A$ (`selection`) が与えられたとき、$u$ を $A$ に対する $t$ の制限とします。重み (`weight`) を返します：

$$
\log \frac{p(r, t; x)}{q(t; u, x) q(r; x, t)}
$$
