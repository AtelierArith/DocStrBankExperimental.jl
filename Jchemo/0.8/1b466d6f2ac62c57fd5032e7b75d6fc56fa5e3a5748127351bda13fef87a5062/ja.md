```
summ(X; digits = 3)
summ(X, y; digits = 3)
```

データセット（または変数）を要約します。

  * `X` : データセット (n, p)。
  * `y` : カテゴリ変数 (n) （クラスメンバーシップ）。
  * `digits` : 出力の桁数。

## 例

```julia
using Jchemo

n = 50
X = rand(n, 3) 
y = rand(1:3, n)
res = summ(X)
@names res
summ(X[:, 2]).res

summ(X, y)
```
