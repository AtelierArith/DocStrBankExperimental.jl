```
elementary_differentials(f::AbstractVector, u, order)
```

ベクトル場 `f` のすべての初等微分を、与えられた `order` までの独立変数 `u` に対して計算します。返される値は、対応する初等微分を取得するために根付き木でインデックス化できます。
