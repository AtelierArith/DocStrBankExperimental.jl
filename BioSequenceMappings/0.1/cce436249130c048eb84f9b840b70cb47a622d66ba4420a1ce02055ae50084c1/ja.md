```
compute_weights(X::AbstractAlignment, θ = 0.2; normalize = true)
```

`X`の配列に対する系統発生的補正重みを計算します。重みの配列`S`は`1/N`であり、ここで`N`は`S`からハミング距離が`H`未満の`X`内の配列の数（`S`自身を含む）です。閾値`H`は`floor(θ⋅L)`であり、ここで`L`は配列の長さです。

返り値はタプル`(weights, Meff)`であり、`Meff`は重みの合計（正規化前）です。`normalize`が`true`の場合、重みは合計が1になるように正規化されます。
