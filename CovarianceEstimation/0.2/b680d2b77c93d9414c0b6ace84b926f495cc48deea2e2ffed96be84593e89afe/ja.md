```
DiagonalCommonVariance
```

線形シュリンクのターゲット：変数の平均分散で乗算された単位行列。`LinearShrinkageTarget`のサブタイプであり、

  * $$
    F_{ij}=v
    $$

    もし $i=j$ の場合、ここで $v=\mathrm{tr}(S)/p$ であり、
  * $$
    F_{ij}=0
    $$

    それ以外の場合
