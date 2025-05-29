```
colmed(X)
```

行列の列ごとの中央値を計算します。

  * `X` : データ (n, p)。

ベクトルを返します。

## 例

```julia
using Jchemo

n, p = 5, 6
X = rand(n, p)

colmed(X)
```
