```
rp(; kwargs...)
rp(X; kwargs...)
rp(X, weights::Weight; kwargs...)
rp!(X::Matrix, weights::Weight; kwargs...)
```

Xデータのランダムプロジェクションを作成します。

  * `X` : Xデータ (n, p)。
  * `weights` : 観測値の重み (n)。`Weight` 型でなければなりません (例えば、関数 `mweight` を参照)。

キーワード引数:

  * `nlv` : `X` が投影される次元の数。
  * `meth` : ランダムプロジェクションの方法。可能な値は `:gauss`、`:li` です。それぞれの関数 `rpmatgauss` と `rpmatli` のキーワード引数を参照してください。
  * `scal` : ブール値。`true` の場合、`X` の各列はその未修正の標準偏差でスケーリングされます。

## 例

```julia
using Jchemo
n, p = (5, 10)
X = rand(n, p)
nlv = 3
meth = :li ; s = sqrt(p) 
#meth = :gauss
model = rp(; nlv, meth, s)
fit!(model, X)
@names model
@names model.fitm
@head model.fitm.T 
@head model.fitm.V 
transf(model, X[1:2, :])
```
