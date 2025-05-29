```
lower_partial_moment(returns, threshold, n, method)
```

この関数は、指定された閾値に対する下部部分モーメント（LPM）を計算します。

# 引数

  * `returns`:     資産のリターンのベクトル。
  * `threshold`:   閾値リターンを示すスカラー値またはベクトル。
  * `n`:           計算する `n`-次モーメント。
  * `method`:      `:full` または `:partial` のいずれか。分母にすべてのリターンの数（`:full`）を使用するか、閾値未満のリターンの数のみ（`:partial`）を使用するかを示します。

# 公式

$$
\text{LPM}_n = \frac{1}{D} \sum_{i=1}^N \max(0, \text{threshold} - \text{returns}_i)^n
$$

ここで、`N` はリターンの数、`D` は分母です。
