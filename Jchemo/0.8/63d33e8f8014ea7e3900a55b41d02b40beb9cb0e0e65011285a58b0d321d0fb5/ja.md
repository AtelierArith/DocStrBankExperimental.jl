```
colnorm(X)
colnorm(X, weights::Weight)
```

行列の列ごとのノルムを計算します。

  * `X` : データ (n, p)。
  * `weights` : 観測値の重み (n)。`Weight` 型でなければなりません (例えば、関数 `mweight` を参照)。

`X` の列 x に対して計算されるノルムは次のとおりです：

  * sqrt(x' * x)

重み付きノルムは次のようになります：

  * sqrt(x' * D * x)、ここで D は `weights.w` の対角行列です。

**警告:** `colnorm(X, mweight(ones(n)))` = `colnorm(X) / sqrt(n)`。

ベクトルを返します。

## 例

```julia
using Jchemo

n, p = 5, 6
X = rand(n, p)
w = mweight(rand(n))

colnorm(X)
colnorm(X, w)
```
