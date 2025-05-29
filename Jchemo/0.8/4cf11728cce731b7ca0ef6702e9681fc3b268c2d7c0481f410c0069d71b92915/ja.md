```
fscale(X, v)
fscale!(X::AbstractMatrix, v)
```

行列の各列をスケーリングします。

  * `X` : データ (n, p)。
  * `v` : スケーリングベクトル (p)。

## 例

```julia
using Jchemo

X = rand(5, 2) 
fscale(X, colstd(X))
```
