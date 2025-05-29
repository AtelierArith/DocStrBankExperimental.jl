```
cosm(X)
cosm(X, Y)
```

コサイン行列を計算します。

  * `X` : データ (n, p)。
  * `Y` : データ (n, q)。

この関数はコサイン行列を計算します：

  * `X` の列のコサイン行列：  ==> (p, p) 行列
  * または `X` と `Y` の列間のコサイン行列：  ==> (p, q) 行列。

## 例

```julia
using Jchemo

n, p = 5, 6
X = rand(n, p)
Y = rand(n, 3)

cosm(X)
cosm(X, Y)
```
