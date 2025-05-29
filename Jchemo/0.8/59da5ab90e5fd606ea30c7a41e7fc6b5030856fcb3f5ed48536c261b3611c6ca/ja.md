```
covm(X)
covm(X, weights::Weight)
covm(X, Y) 
covm(X, Y, weights::Weight)
```

重み付き共分散行列を計算します。

  * `X` : データ (n, p)。
  * `Y` : データ (n, q)。
  * `weights` : 観測値の重み (n)。`Weight` 型のオブジェクト（例えば、関数 `mweight` によって生成される）。

この関数は、修正されていない共分散行列を計算します：

  * `X` の列の共分散：  ==> (p, p) 行列
  * または `X` と `Y` の列間の共分散：  ==> (p, q) 行列。

## 例

```julia
using Jchemo

n, p = 5, 6
X = rand(n, p)
Y = rand(n, 3)
w = mweight(rand(n))

covm(X, w)
covm(X, Y, w)
```
