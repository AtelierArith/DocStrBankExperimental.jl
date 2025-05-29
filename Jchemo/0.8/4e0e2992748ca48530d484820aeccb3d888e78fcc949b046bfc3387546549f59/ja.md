```
rownorm(X)
```

行ごとのノルムを計算します。

  * `X` : データ (n, p)。

`X` の行 x に対して計算されるノルムは次の通りです：

  * sqrt(x' * x)

ベクトルを返します。

注：@mcabbott に感謝します https://discourse.julialang.org/t/orders-of-magnitude-runtime-difference-in-row-wise-norm/96363。

## 例

```julia
using Jchemo

n, p = 5, 6
X = rand(n, p)

rownorm(X)
```
