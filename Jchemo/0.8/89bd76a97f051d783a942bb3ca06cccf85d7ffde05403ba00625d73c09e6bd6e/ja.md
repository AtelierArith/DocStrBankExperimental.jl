```
sampks(X, k::Int; metric = :eucl)
```

Kennard-Stoneサンプリングによるトレーニングセットとテストセットの構築。  

  * `X` : Xデータ (n, p)。
  * `k` : サンプリングするテスト観測の数。

キーワード引数: 

  * `metric` : 距離計算に使用されるメトリック。可能な値は: `:eucl` (ユークリッド)、`：mah` (マハラノビス)。

2つの出力（データの行インデックス）が返されます: 

  * `train` (`n` - `k`),
  * `test` (`k`)。

出力`test`はKennard-Stone (KS)アルゴリズム（Kennard & Stone, 1969）から構築されます。 

**注意:** 構造上、KSサンプリングによって選択された観測のセットは、残りの観測のセットよりも高い変動性を含みます。画期的な記事（K&S, 1969）では、アルゴリズムはキャリブレーションセットを構築するために使用される観測を選択するために使用されます。対照的に、現在の関数では、KSはトレーニングセットよりも高い変動性を持つテストセットを選択するために使用されます。 

## 参考文献

Kennard, R.W., Stone, L.A., 1969. Computer aided design of experiments.  Technometrics, 11(1), 137-148.

## 例

```julia
using Jchemo, JchemoData, JLD2, CairoMakie
path_jdat = dirname(dirname(pathof(JchemoData)))
db = joinpath(path_jdat, "data/cassav.jld2") 
@load db dat
@names dat

X = dat.X 
y = dat.Y.tbc

k = 80
res = sampks(X, k)
@names res
res.train 
res.test

model = pcasvd(nlv = 15) 
fit!(model, X) 
@head T = model.fitm.T
res = sampks(T, k; metric = :mah)

#####################

n = 10
k = 25 
X = [repeat(1:n, inner = n) repeat(1:n, outer = n)] 
X = Float64.(X) 
X .= X + .1 * randn(nro(X), nco(X))
s = sampks(X, k).test
f, ax = plotxy(X[:, 1], X[:, 2])
scatter!(ax, X[s, 1], X[s, 2]; color = "red") 
f
```
