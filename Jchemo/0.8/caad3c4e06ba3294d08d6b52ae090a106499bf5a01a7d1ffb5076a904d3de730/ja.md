```
colmad(X)
```

行列の列ごとの中央値絶対偏差 (MAD) を計算します。

  * `X` : データ (n, p)。

ベクトルを返します。

## 例

```julia
using Jchemo

n, p = 5, 6
X = rand(n, p)

colmad(X)
```
