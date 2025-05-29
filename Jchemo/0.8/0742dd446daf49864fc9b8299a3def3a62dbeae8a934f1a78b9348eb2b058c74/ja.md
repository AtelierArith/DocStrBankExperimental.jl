```
fcenter(X, v)
fcenter!(X::AbstractMatrix, v)
```

行列の各列を中心化します。

  * `X` : データ (n, p)。
  * `v` : 中心化ベクトル (p)。

## 例

```julia
using Jchemo

n, p = 5, 6
X = rand(n, p)
xmeans = colmean(X)
fcenter(X, xmeans)
```
