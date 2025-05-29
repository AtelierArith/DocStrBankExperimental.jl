```
splsr(; kwargs...)
splsr(X, Y; kwargs...)
splsr(X, Y, weights::Weight; kwargs...)
splsr!(X::Matrix, Y::Union{Matrix, BitMatrix}, weights::Weight; kwargs...)
```

スパース部分最小二乗回帰 (Lê Cao et al. 2008)

  * `X` : Xデータ (n, p)。
  * `Y` : Yデータ (n, q)。
  * `weights` : 観測値の重み (n)。    `Weight` 型でなければなりません (例えば、関数 `mweight` を参照)。

キーワード引数:

  * `nlv` : 計算する潜在変数 (LV) の数。
  * `meth` : スパースしきい値処理に使用される方法。    可能な値は: `:soft`, `:hard`。以下を参照してください。
  * `nvar` : 各 LV に選択される変数 (`X` 列) の数。    単一の整数 (すなわち、各 LV に対して同じ数の変数) であるか、    または長さ `nlv` のベクトルであることができます。
  * `scal` : ブール値。`true` の場合、`X` と `Y` の各列は    補正されていない標準偏差でスケーリングされます。

Lê Cao et al. 2008 のスパース部分最小二乗回帰アルゴリズムの適応版。Dayal & McGregor (1997) の高速「改良カーネルアルゴリズム #1」が Nipals の代わりに使用されます。

現在の `splsr` バージョンでは、スパースしきい値処理は `X` のみに関係します。この関数は、スパース `X` ローディング重み w を計算するための2つのしきい値処理方法を提供します (`:soft` と `:hard`)、説明については関数 `spca` を参照してください。

`meth = :soft` の場合、R パッケージ mixOmics の関数 `spls` (Lê Cao et al.) と同じ結果が返され、回帰モードで `Y` に対してスパース性はありません。

Roger et al 2011 で説明されている COVSEL 回帰法 (Höskuldsson 1992 も参照) は、`nvar = 1` を設定することで実装されています。

## 参考文献

Dayal, B.S., MacGregor, J.F., 1997. Improved PLS algorithms.  Journal of Chemometrics 11, 73-85.

Höskuldsson, A., 1992. The H-principle in modelling with applications  to chemometrics. Chemometrics and Intelligent Laboratory Systems,  Proceedings of the 2nd Scandinavian Symposium on Chemometrics 14,  139–153. https://doi.org/10.1016/0169-7439(92)80099-P

Lê Cao, K.-A., Rossouw, D., Robert-Granié, C., Besse, P., 2008.  A Sparse PLS for Variable Selection when Integrating Omics Data.  Statistical Applications in Genetics and Molecular Biology 7.  https://doi.org/10.2202/1544-6115.1390

Kim-Anh Lê Cao, Florian Rohart, Ignacio Gonzalez, Sebastien Dejean  with key contributors Benoit Gautier, Francois Bartolo, contributions  from Pierre Monget, Jeff Coquery, FangZou Yao and Benoit Liquet.  (2016). mixOmics: Omics Data Integration Project. R package  version 6.1.1. https://www.bioconductor.org/packages/release/bioc/html/mixOmics.html

Bioconductor のパッケージ mixOmics: https://www.bioconductor.org/packages/release/bioc/html/mixOmics.html

Roger, J.M., Palagos, B., Bertrand, D., Fernandez-Ahumada, E., 2011.  covsel: Variable selection for highly multivariate and multi-response  calibration: Application to IR spectroscopy.  Chem. Lab. Int. Syst. 106, 216-223.

## 例

```julia
using Jchemo, JchemoData, JLD2, CairoMakie
path_jdat = dirname(dirname(pathof(JchemoData)))
db = joinpath(path_jdat, "data/cassav.jld2") 
@load db dat
@names dat
X = dat.X 
y = dat.Y.tbc
year = dat.Y.year
tab(year)
s = year .<= 2012
Xtrain = X[s, :]
ytrain = y[s]
Xtest = rmrow(X, s)
ytest = rmrow(y, s)

nlv = 15
meth = :soft
#meth = :hard
nvar = 20
model = splsr(; nlv, meth, nvar) ;
fit!(model, Xtrain, ytrain)
@names model
@names model.fitm
@head model.fitm.T
@head model.fitm.W

coef(model)
coef(model; nlv = 3)

@head transf(model, Xtest)
@head transf(model, Xtest; nlv = 3)

res = predict(model, Xtest)
@head res.pred
@show rmsep(res.pred, ytest)
plotxy(res.pred, ytest; color = (:red, .5), bisect = true, xlabel = "Prediction", 
    ylabel = "Observed").f    

res = summary(model, Xtrain) ;
@names res
z = res.explvarx
plotgrid(z.nlv, z.cumpvar; step = 2, xlabel = "Nb. LVs", 
    ylabel = "Prop. Explained X-Variance").f
```
