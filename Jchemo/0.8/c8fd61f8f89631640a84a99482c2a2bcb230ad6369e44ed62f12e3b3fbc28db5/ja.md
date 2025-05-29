```
rowstd(X)
```

行ごとの標準偏差（修正なし）を計算します。

  * `X` : データ (n, p)。

ベクトルを返します。

## 例

```julia
using Jchemo

n, p = 5, 6
X = rand(n, p)
rowstd(X)
```
