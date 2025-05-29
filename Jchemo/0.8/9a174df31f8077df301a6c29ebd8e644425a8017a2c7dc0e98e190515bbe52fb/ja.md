```
fcscale(X, u, v)
fcscale!(X, u, v)
```

行列の各列をセンタリングし、スケーリングします。

  * `X` : データ (n, p)。
  * `u` : センタリングベクトル (p)。
  * `v` : スケーリングベクトル (p)。

## 例

```julia
using Jchemo

n, p = 5, 6
X = rand(n, p)
xmeans = colmean(X)
xscales = colstd(X)
fcscale(X, xmeans, xscales)
```
