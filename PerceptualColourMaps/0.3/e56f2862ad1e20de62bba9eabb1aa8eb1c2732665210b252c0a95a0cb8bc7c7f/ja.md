bbspline - 基本Bスプライン

```
Usage:  S = bbspline(P, k, N)

Arguments:   P - [dim x Npts] 制御点の配列
             k - スプラインの次数 (>= 2).
                 k = 2: 線形
                 k = 3: 二次, など
             N - スプラインに沿って評価する点のオプション数。
                 デフォルトは100。

Returns:     S - スプライン曲線  [dim x N] スプライン点
```

See also: pbspline
