```
upside_deviation(returns, threshold; method=:full)
```

上向き偏差（アップサイドデビエーション）、またはセミスタンダード偏差を計算し、上向きの「リスク」を捉えます。

# 引数

  * `returns`:     資産のリターンのベクトル。
  * `threshold`:   スカラー値または閾値リターンを示すベクトル。
  * `method`:      `:full`（デフォルト）または `:partial` のいずれか。分母にすべてのリターンの数（`:full`）を使用するか、閾値を超えるリターンの数（`:partial`）のみを使用するかを示します。

# 数式

$$
\text{Upside Deviation} = \sqrt{\text{Higher Partial Moment}}
$$
