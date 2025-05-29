```
colwise!(metric::PreMetric, r::AbstractArray, a, b)
```

距離 `metric` に従って、反復可能なコレクション `a` と `b` の対応する要素間の距離を計算し、その結果を `r` に格納します。

`a` と `b` は同じ数の要素を持たなければならず、`r` は `length(a) == length(b)` の長さの配列でなければなりません。
