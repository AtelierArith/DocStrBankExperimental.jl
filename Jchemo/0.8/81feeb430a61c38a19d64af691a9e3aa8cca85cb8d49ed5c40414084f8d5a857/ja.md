```
cca(; kwargs...)
cca(X, Y; kwargs...)
cca(X, Y, weights::Weight; kwargs...)
cca!(X::Matrix, Y::Matrix, weights::Weight; kwargs...)
```

正準相関分析 (CCA, RCCA)。

  * `X` : 最初のデータブロック。
  * `Y` : 2番目のデータブロック。
  * `weights` : 観測の重み (n)。 `Weight` 型でなければなりません (例えば、関数 `mweight` を参照)。

キーワード引数:

  * `nlv` : 計算する潜在変数 (LVs = スコア) の数。
  * `bscal` : ブロックスケーリングのタイプ。可能な値は `:none`, `:frob` です。関数 `blockscal` を参照してください。
  * `tau` : 正則化パラメータ (∊ [0, 1])。
  * `scal` : ブール値。 `true` の場合、ブロック `X` と `Y` の各列は、その未修正の標準偏差でスケーリングされます (ブロックスケーリングの前)。

この関数は、SVD分解を使用したCCAアルゴリズムを実装しており、Weenink 2003のセクション2で提示されています。

連続正則化が利用可能です (パラメータ `tau`)。ブロックの中心化とスケーリングの後、関数はブロックLV (TxおよびTy) を返します。これは、次のように定義されるProjx * ProjyおよびProjy * Projxの固有ベクトルに比例します。

  * Cx = (1 - `tau`) * X'DX + `tau` * Ix
  * Cy = (1 - `tau`) * Y'DY + `tau` * Iy
  * Cxy = X'DY
  * Projx = sqrt(D) * X * invCx * X' * sqrt(D)
  * Projy = sqrt(D) * Y * invCx * Y' * sqrt(D)

ここで、Dは観測 (行) メトリックです。値 `tau` = 0 は、共分散行列を逆転させる際に不安定性を引き起こす可能性があります。しばしば、擬似逆行列と同様の結果を得るために、イプシロン値 (例えば、`tau` = 1e-8) を使用する方が良い代替手段です。

正規化された後 (および均一な `weights` を使用して)、関数によって返されるスコアは、Rパッケージ `CCA` (González et al.) および `mixOmics` (Lê Cao et al.) の関数 `rcc` によって返されるものと同じであることが期待されます。これらのパラメータ lambda1 および lambda2 は次のように設定されます。

  * lambda1 = lambda2 = `tau` / (1 - `tau`) * n / (n - 1)

`summary` 出力の詳細については、関数 `plscan` を参照してください。

## 参考文献

González, I., Déjean, S., Martin, P.G.P., Baccini, A., 2008. CCA: An R Package to Extend Canonical Correlation Analysis. Journal of Statistical Software 23, 1-14. https://doi.org/10.18637/jss.v023.i12

Hotelling, H. (1936): “Relations between two sets of variates”, Biometrika 28: pp. 321–377.

Lê Cao, K.-A., Rohart, F., Gonzalez, I., Dejean, S., Abadi, A.J., Gautier, B., Bartolo, F., Monget, P.,  Coquery, J., Yao, F., Liquet, B., 2022. mixOmics: Omics Data Integration Project.  https://doi.org/10.18129/B9.bioc.mixOmics

Weenink, D. 2003. Canonical Correlation Analysis, Institute of Phonetic Sciences, Univ. of Amsterdam,  Proceedings 25, 81-99.

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

nlv = 3
bscal = :frob ; tau = 1e-8
model = cca(; nlv, bscal, tau)
fit!(model, X, Y)
@names model
@names model.fitm

@head model.fitm.Tx
@head transfbl(model, X, Y).Tx

@head model.fitm.Ty
@head transfbl(model, X, Y).Ty

res = summary(model, X, Y) ;
@names res
res.cortx2ty
res.rvx2tx
res.rvy2ty
res.rdx2tx
res.rdy2ty
res.corx2tx 
res.cory2ty 
```
