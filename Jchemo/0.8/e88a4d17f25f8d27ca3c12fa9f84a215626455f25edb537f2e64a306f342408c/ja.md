```
matB(X, y, weights::Weight)
```

クラス間共分散行列。

  * `X` : Xデータ (n, p)。
  * `y` : クラスメンバーシップを定義するベクトル (n)。
  * `weights` : 観測値の重み (n)。タイプ `Weight` でなければなりません (例えば、関数 `mweight` を参照)。

`X` のクラス間共分散行列 (出力 `B`) を計算します。これは、重み付きクラス中心の（非修正）共分散行列です。

## 例

```julia
using Jchemo, StatsBase

n = 20 ; p = 3
X = rand(n, p)
y = rand(1:3, n)
tab(y) 
weights = mweight(ones(n)) 

res = matB(X, y, weights) ;
res.B
res.priors
res.ni
res.lev

res = matW(X, y, weights) ;
res.W
res.Wi

matW(X, y, weights).W + matB(X, y, weights).B
cov(X; corrected = false)

v = mweight(collect(1:n))
matW(X, y, v).priors 
matB(X, y, v).priors 
matW(X, y, v).W + matB(X, y, v).B
covm(X, v)
```
