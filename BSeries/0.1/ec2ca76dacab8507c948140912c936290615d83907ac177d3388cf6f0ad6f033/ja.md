```
elementary_differentials(fs::NTuple{2, AbstractVector}, u, order)
```

2つのベクトル場 `f` の和のすべての初等微分を、与えられた `order` まで独立変数 `u` に対して計算します。返される値は、対応する初等微分を取得するために (二色) 根付き木でインデックス化できます。
