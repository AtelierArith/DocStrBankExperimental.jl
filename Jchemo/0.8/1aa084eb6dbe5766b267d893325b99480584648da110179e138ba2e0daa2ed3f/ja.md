```
spca(; kwargs...)
spca(X; kwargs...)
spca(X, weights::Weight; kwargs...)
spca!(X::Matrix, weights::Weight; kwargs...)
```

スパースPCA（Shen & Huang 2008）。

  * `X` : Xデータ (n, p)。
  * `weights` : 観測値の重み (n)。    `Weight` 型でなければなりません（例えば、関数 `mweight` を参照）。

キーワード引数：

  * `nlv` : 主成分 (PC) の数。
  * `meth` : スパースしきい値処理に使用される方法。    可能な値は `:soft`, `:hard` です。以下を参照してください。
  * `nvar` : 各主成分 (PC) に選択される変数 (`X`-列) の数。単一の整数（すなわち、各PCに対して同じ数の変数）または長さ `nlv` のベクトルであることができます。
  * `defl` : `X`-行列のデフレーションのタイプ、以下を参照。
  * `tol` : Nipals反復の停止のための許容値。
  * `maxit` : Nipals反復の最大数。
  * `scal` : ブール値。`true` の場合、`X` の各列はその未修正の標準偏差でスケーリングされます。

sPCA-rSVDアルゴリズム（正則化された低ランク行列近似）Shen & Huang 2008。

このアルゴリズムは、しきい値処理のステップを含む最小二乗回帰（Nipals）を交互に行うことによって、各負荷ベクトルを反復的に計算します。関数 `spca` は、Shen & Huang 2008の補題2で報告されたしきい値処理方法 '1' と '2'（`:soft` と `:hard`）を提供します：

  * Shen & Huang 2008 によって使用される調整パラメータは、負荷ベクトル内のゼロ要素の数であり、スパース性の度合いと呼ばれます。逆に、現在の関数 `spca` は非ゼロ要素の数（`nvar`）を使用し、これは p - スパース性の度合いに等しいです。
  * しきい値処理関数内で使用されるカットオフ 'lambda' の計算方法については、関数 `snipals_shen` のコードを参照してください（Shen & Huang 2008）。`nvar` の値が与えられた場合、負荷ベクトル内に tied 値があると、他のソフトウェアとの違いが生じる可能性があります（分位数を計算するために使用される方法の選択に依存します）。

行列 `X` は2つの方法でデフレートできます：

  * `defl = :v` : 行列 `X` は、負荷ベクトル `v` に対する `X'`-列の回帰によってデフレートされます。これは、Shen & Huang 2008 によって提案された方法です（定理 A.2 p.1033 を参照）。
  * `defl = :t` : 行列 `X` は、スコアベクトル `t` に対する `X`-列の回帰によってデフレートされます。これは、Rパッケージ `mixOmics` の関数 `spca` で使用される方法です（Le Cao et al. 2016）。

各PCによってXで説明される%分散の計算方法（関数 `summary` によって返される）は、選択されたデフレーションのタイプに依存します（コードを参照）。

## 参考文献

Kim-Anh Lê Cao, Florian Rohart, Ignacio Gonzalez, Sebastien  Dejean と主要な貢献者 Benoit Gautier, Francois Bartolo,  Pierre Monget, Jeff Coquery, FangZou Yao 及び Benoit Liquet. (2016). mixOmics: Omicsデータ統合プロジェクト. Rパッケージバージョン 6.1.1.  https://www.bioconductor.org/packages/release/bioc/html/mixOmics.html

Shen, H., Huang, J.Z., 2008. スパース主成分分析を正則化された低ランク行列近似を通じて行う.  Journal of Multivariate Analysis 99, 1015–1034.  https://doi.org/10.1016/j.jmva.2007.06.007

## 例

```julia
using Jchemo, JchemoData, JLD2 
path_jdat = dirname(dirname(pathof(JchemoData)))
db = joinpath(path_jdat, "data/iris.jld2") 
@load db dat
@names dat
@head dat.X
X = dat.X[:, 1:4]
n = nro(X)
ntest = 30
s = samprand(n, ntest) 
Xtrain = X[s.train, :]
Xtest = X[s.test, :]

nlv = 3 
meth = :soft
#meth = :hard
nvar = 2
model = spca(; nlv, meth, nvar) ;
fit!(model, Xtrain) 
fitm = model.fitm ;
@names fitm
fitm.niter
fitm.sellv 
fitm.sel
V = fitm.V
V' * V
@head T = fitm.T
T' * T
@head transf(model, Xtrain)

@head Ttest = transf(fitm, Xtest)

res = summary(model, Xtrain) ;
res.explvarx
```
