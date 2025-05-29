```
corm(X) 
corm(X, Y) 
corm(X, weights::Weight)
corm(X, Y, weights::Weight)
```

重み付き相関行列を計算します。

  * `X` : データ (n, p)。
  * `Y` : データ (n, q)。
  * `weights` : 観測値の重み (n)。`Weight` 型のオブジェクト（例えば、関数 `mweight` によって生成されたもの）。

未修正の相関行列 

  * `X`-列の :  ==> (p, p) 行列
  * または `X`-列と `Y`-列の間の :  ==> (p, q) 行列。

## 例

```julia
using Jchemo

n, p = 5, 6
X = rand(n, p)
Y = rand(n, 3)
w = mweight(rand(n))

corm(X, w)
corm(X, Y, w)
```
