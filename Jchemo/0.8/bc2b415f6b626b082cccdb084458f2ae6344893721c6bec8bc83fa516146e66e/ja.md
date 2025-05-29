```
ccawold(; kwargs...)
ccawold(X, Y; kwargs...)
ccawold(X, Y, weights::Weight; kwargs...)
ccawold!(X::Matrix, Y::Matrix, weights::Weight; kwargs...)
```

正準相関分析 (CCA, RCCA) - Wold Nipals アルゴリズム。

  * `X` : 最初のデータブロック。
  * `Y` : 2番目のデータブロック。
  * `weights` : 観測値の重み (n)。タイプ `Weight` でなければなりません (例: 関数 `mweight` を参照)。

キーワード引数:

  * `nlv` : 計算する潜在変数 (LVs = スコア) の数。
  * `bscal` : ブロックスケーリングのタイプ。可能な値は: `:none`, `:frob`。関数 `blockscal` を参照。
  * `tau` : 正則化パラメータ (∊ [0, 1])。
  * `tol` : 収束のための許容値 (Nipals)。
  * `maxit` : 最大反復回数 (Nipals)。
  * `scal` : ブール値。`true` の場合、ブロック `X` と `Y` の各列は、その未修正の標準偏差でスケーリングされます (ブロックスケーリングの前)。

この関数は、Tenenhaus 1998 p.204 に示された Nipals ccawold アルゴリズムを実装しています (Wold et al. 1984 に関連)。

この実装では、LVs 計算の各ステップの後に、X と Y はそれぞれのスコア (tx と ty) に対してデフレートされます。

連続正則化が利用可能です (パラメータ `tau`)。ブロックの中心化とスケーリングの後、共分散行列は次のように計算されます:

  * Cx = (1 - `tau`) * X'DX + `tau` * Ix
  * Cy = (1 - `tau`) * Y'DY + `tau` * Iy

ここで D は観測 (行) メトリックです。値 `tau` = 0 は共分散行列を逆転させる際に不安定性を引き起こす可能性があります。しばしば、擬似逆行列と同様の結果を得るために、イプシロン値 (例: `tau` = 1e-8) を使用する方が良い代替手段です。

関数によって返される正規化されたスコアは、均一な `weights` を使用して、R パッケージ `RGCCA` の関数 `rgcca` によって返されるものと同じであることが期待されます (Tenenhaus & Guillemot 2017, Tenenhaus et al. 2017)。

`summary` 出力の詳細については関数 `plscan` を参照してください。`summary` 出力の詳細については関数 `plscan` を参照してください。

## 参考文献

Tenenhaus, A., Guillemot, V. 2017. RGCCA: 正則化およびスパース一般化正準相関分析のための多ブロックデータ分析。 https://cran.r-project.org/web/packages/RGCCA/index.html 

Tenenhaus, M., 1998. La régression PLS: théorie et pratique. Editions Technip, Paris.

Tenenhaus, M., Tenenhaus, A., Groenen, P.J.F., 2017. 正則化された一般化正準相関分析: 逐次多ブロック成分法のためのフレームワーク。 Psychometrika 82, 737–777. https://doi.org/10.1007/s11336-017-9573-x

Wold, S., Ruhe, A., Wold, H., Dunn, III, W.J., 1984. 線形回帰における共線性の問題。一般化逆行列への部分最小二乗 (PLS) アプローチ。 SIAM Journal on Scientific and Statistical Computing 5, 735–743. https://doi.org/10.1137/0905052

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
model = ccawold(; nlv, bscal, tau, tol = 1e-10)
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
