```
fweight(X, v)
fweight!(X::AbstractMatrix, v)
```

行列の各行に重みを付けます。

  * `X` : データ (n, p)。
  * `v` : 重みベクトル (n)。

## 例

```julia
using Jchemo, LinearAlgebra

X = rand(5, 2) 
w = rand(5) 
fweight(X, w)
diagm(w) * X

fweight!(X, w)
X
```
