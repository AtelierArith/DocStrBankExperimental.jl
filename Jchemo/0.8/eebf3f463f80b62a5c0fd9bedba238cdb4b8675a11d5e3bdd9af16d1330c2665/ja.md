```
rda(; kwargs...)
rda(X, y; kwargs...)
rda(X, y, weights::Weight; kwargs...)
```

正則化判別分析 (RDA)。

  * `X` : Xデータ (n, p)。
  * `y` : 単変量クラスメンバーシップ (n)。
  * `weights` : 観測値の重み (n)。`Weight` 型でなければなりません (例えば、関数 `mweight` を参照)。

キーワード引数:

  * `prior` : クラスメンバーシップの事前確率のタイプ。可能な値は: `:prop` (比例)、`：unif` (一様)、または各クラスの事前重みを与えるベクトル (ベクトルの場合、`mlev(y)` と同じ順序でソートされている必要があります)。
  * `alpha` : QDA (`alpha = 0`) と LDA (`alpha = 1`) の間の連続体を定義するスカラー (∈ [0, 1])。
  * `lb` : リッジ正則化パラメータ "lambda" (>= 0)。
  * `simpl` : ブール値。関数 `dmnorm` を参照。
  * `scal` : ブール値。`true` の場合、`X` の各列はその未修正標準偏差でスケーリングされます。

W を (修正された) プール内クラス共分散行列、Wi をクラス i の (修正された) 内部クラス共分散行列とします。正則化は次の2つの連続したステップによって行われます (各クラス i に対して):

1. QDA と LDA の間の連続体: Wi(1) = (1 - `alpha`) * Wi + `alpha` * W
2. リッジ正則化: Wi(2) = Wi(1) + `lb` * I

その後、QDA アルゴリズムは行列 {Wi(2)} に対して実行されます。

関数 `rda` は、Friedman 1989 によって使用された正則化式とはわずかに異なります (Eq.18): 選択は共分散行列 Wi(2) を単位行列の対角線に縮小することです (リッジ正則化; 例えば、Guo et al. 2007)。

特別なケース:

  * `alpha` = 1 & `lb` = 0 : LDA
  * `alpha` = 0 & `lb` = 0 : QDA
  * `alpha` = 1 & `lb` > 0 : 対角正則化行列を持つペナルティ付き LDA (Hastie et al 1995)

他の詳細については、関数 `lda` と `qda` を参照してください (引数 `weights` と `prior`)。

## 参考文献

Friedman JH. Regularized Discriminant Analysis. Journal of the American Statistical Association. 1989;  84(405):165-175. doi:10.1080/01621459.1989.10478752.

Guo Y, Hastie T, Tibshirani R. Regularized linear discriminant analysis and its application in microarrays.  Biostatistics. 2007; 8(1):86-100. doi:10.1093/biostatistics/kxj035.

Hastie, T., Buja, A., Tibshirani, R., 1995. Penalized Discriminant Analysis. The Annals of Statistics 23, 73–102.

## 例

```julia
using Jchemo, JchemoData, JLD2
path_jdat = dirname(dirname(pathof(JchemoData)))
db = joinpath(path_jdat, "data/iris.jld2")
@load db dat
@names dat
@head dat.X
X = dat.X[:, 1:4]
y = dat.X[:, 5]
n = nro(X)
ntest = 30
s = samprand(n, ntest)
Xtrain = X[s.train, :]
ytrain = y[s.train]
Xtest = X[s.test, :]
ytest = y[s.test]
ntrain = n - ntest
(ntot = n, ntrain, ntest)
tab(ytrain)
tab(ytest)

alpha = .5
lb = 1e-8
model = rda(; alpha, lb)
fit!(model, Xtrain, ytrain)
@names model
@names fitm = model.fitm
fitm.lev
fitm.ni

res = predict(model, Xtest) ;
@names res
@head res.posterior
@head res.pred
errp(res.pred, ytest)
conf(res.pred, ytest).cnt
```
