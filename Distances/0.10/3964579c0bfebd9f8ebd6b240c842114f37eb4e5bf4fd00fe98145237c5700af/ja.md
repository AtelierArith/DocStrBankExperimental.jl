```
colwise(metric::PreMetric, a, b)
```

イテラブルコレクション `a` と `b` の対応する要素間の距離を、距離 `metric` に従って計算します。

`a` と `b` は同じ数の要素を持っている必要があります（`length(a) == length(b)`）。
