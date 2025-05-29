```
downside_deviation(returns, threshold; method=:full)
```

ダウンサイドデビエーション（下振れ偏差）を計算します。これは、下振れリスクを捉えるセミスタンダード偏差とも呼ばれます。

# 引数

  * `returns`:     資産のリターンのベクトル。
  * `threshold`:   スカラー値または閾値リターンを示すベクトル。
  * `method`:      `:full`（デフォルト）または `:partial` のいずれか。分母にすべてのリターンの数（`:full`）を使用するか、閾値未満のリターンの数（`:partial`）のみを使用するかを示します。

# 数式

$$
\text{Downside Deviation} = \sqrt{\text{Lower Partial Moment}}
$$
