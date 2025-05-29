```
mad(x; center=median(x), normalize=true)
```

コレクション `x` の中央値（デフォルトでは中央値の周り）に対する中央値絶対偏差（MAD）を計算します。

`normalize` が `true` に設定されている場合、MAD は `1 / quantile(Normal(), 3/4) ≈ 1.4826` で乗算され、データが正規分布しているという仮定の下で標準偏差の一貫した推定量を得るために使用されます。
