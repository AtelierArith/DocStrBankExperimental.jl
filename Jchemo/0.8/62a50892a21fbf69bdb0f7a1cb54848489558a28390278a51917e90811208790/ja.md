```
dupl(X; digits = 3)
```

データセット内の重複行を見つけます。

  * `X` : データセット。
  * `digits` : チェックする前に `X` を丸めるために使用される桁数。

## 例

```julia
using Jchemo

X = rand(5, 3)
Z = vcat(X, X[1:3, :], X[1:1, :])
dupl(X)
dupl(Z)

M = hcat(X, fill(missing, 5))
Z = vcat(M, M[1:3, :])
dupl(M)
dupl(Z)
```
