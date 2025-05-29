```
rasvd(; kwargs...)
rasvd(X, Y; kwargs...)
rasvd(X, Y, weights::Weight; kwargs...)
rasvd!(X::Matrix, Y::Matrix, weights::Weight; kwargs...)
```

冗長性分析（RA）、すなわち計器変数に関する主成分分析（PCAIV）

  * `X` : 最初のデータブロック。
  * `Y` : 2番目のデータブロック。
  * `weights` : 観測値の重み（n）。`Weight`型でなければなりません（例えば、関数`mweight`を参照）。

キーワード引数：

  * `nlv` : 計算する潜在変数（LVs = スコア）の数。
  * `bscal` : ブロックスケーリングのタイプ。可能な値は： `:none`, `:frob`。関数`blockscal`を参照。
  * `tau` : 正則化パラメータ（∊ [0, 1]）。
  * `scal` : ブール値。`true`の場合、ブロック`X`および`Y`の各列は、その未修正の標準偏差でスケーリングされます（ブロックスケーリングの前に）。

例えば、Bougeard et al. 2011a,bおよびLegendre & Legendre 2012を参照してください。Y*hatを`Y`を`X`に回帰させたフィッティング値とします。スコア`Ty`はY*hatのPCAスコアです。スコア`Tx`は`Ty`を`X`に回帰させたフィッティング値です。

連続正則化が利用可能です。ブロックの中心化とスケーリングの後、共分散行列は次のように計算されます：

  * Cx = (1 - `tau`) * X'DX + `tau` * Ix

ここでDは観測（行）メトリックです。値`tau` = 0は共分散行列を逆転させる際に不安定性を引き起こす可能性があります。一般的には、擬似逆行列と同様の結果を得るために、イプシロン値（例えば、`tau` = 1e-8）を使用する方が良い選択です。

## 参考文献

Bougeard, S., Qannari, E.M., Lupo, C., Chauvin, C., 2011-a. ユーザーの視点からのマルチブロック冗長性分析。獣医学疫学への応用。電子応用統計分析ジャーナル 4, 203-214. https://doi.org/10.1285/i20705948v4n2p203

Bougeard, S., Qannari, E.M., Rose, N., 2011-b. マルチブロック冗長性分析：解釈ツールと疫学への応用。ケモメトリクスジャーナル 25, 467-475. https://doi.org/10.1002/cem.1392

Legendre, V., Legendre, L., 2012. 数値生態学。エルゼビア、アムステルダム、オランダ。

Tenenhaus, A., Guillemot, V. 2017. RGCCA：マルチブロックデータのための正則化およびスパース一般化共分散分析。 https://cran.r-project.org/web/packages/RGCCA/index.html 

## 例

```julia
using Jchemo, JchemoData, JLD2
mypath = dirname(dirname(pathof(JchemoData)))
db = joinpath(mypath, "data", "linnerud.jld2") 
@load db dat
@names dat
X = dat.X
Y = dat.Y
n, p = size(X)
q = nco(Y)

nlv = 2
bscal = :frob ; tau = 1e-4
model = rasvd(; nlv, bscal, tau)
fit!(model, X, Y)
@names model
@names model.fitm

@head model.fitm.Tx
@head transfbl(model, X, Y).Tx

@head model.fitm.Ty
@head transfbl(model, X, Y).Ty

res = summary(model, X, Y) ;
@names res
res.explvarx
res.explvary
res.cortx2ty
res.rvx2tx
res.rvy2ty
res.rdx2tx
res.rdy2ty
res.corx2tx 
res.cory2ty 
```
