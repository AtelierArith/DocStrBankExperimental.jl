```
rowmean(X)
```

行ごとの平均を計算します。

  * `X` : データ (n, p)。

ベクトルを返します。

## 例

```julia
using Jchemo

n, p = 5, 6
X = rand(n, p)
rowmean(X)
```
