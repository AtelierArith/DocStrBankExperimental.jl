```
fda(; kwargs...)
fda(X, y; kwargs...)
fda(X, y, weights; kwargs...)
fda!(X::Matrix, y, weights; kwargs...)
```

階層的判別分析 (FDA)。

  * `X` : Xデータ (n, p)。
  * `y` : yデータ (n) (クラスメンバーシップ)。
  * `weights` : 観測値の重み (n)。`Weight` 型でなければなりません (例えば、関数 `mweight` を参照)。

キーワード引数:

  * `nlv` : 判別成分の数。
  * `lb` : リッジ正則化パラメータ "lambda"。`X` に共線性がある場合に使用できます。
  * `prior` : クラスメンバーシップのための事前確率のタイプ。可能な値は: `:unif` (一様)、`:prop` (比例)、または各クラスの事前重みを与えるベクトル (ベクトルの場合、`mlev(y)` と同じ順序にソートされている必要があります)。
  * `scal` : ブール値。`true` の場合、`X` の各列はその未修正の標準偏差でスケーリングされます。

FDAは、逆行列(W) * Bの固有因子分解によって行われます。ここで、Wは「内部」共分散行列 (クラス間でプールされた) であり、Bは「外部」共分散行列です。

この関数は合意を最大化します:

  * p'Bp / p'Wp

すなわち、制約 p'Wp = 1 のもとで p'Bp を最大化します。ベクトル p (行列 `V` の列) は、しばしば「LD」と呼ばれる線形判別係数です。

`X` が条件不良の場合、リッジ正則化を使用できます:

  * `lb` > 0 の場合、W は W + `lb` * I に置き換えられます。ここで、I は単位行列です。

現在の関数の高レベルバージョンでは、観測重みは与えられた事前確率 (引数 `prior`) によって自動的に定義されます: 観測重みのクラスごとの小計は事前確率と等しく設定されます。低レベルバージョン (引数 `weights`) は他の選択肢を実装することを可能にします。

## 例

```julia
using Jchemo, JchemoData, JLD2, CairoMakie 
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
tab(ytrain)
tab(ytest)

nlv = 2
model = fda(; nlv)
#model = fdasvd(; nlv)
fit!(model, Xtrain, ytrain)
@names model
@names model.fitm
fitm = model.fitm ;
lev = fitm.lev
nlev = length(lev)
fitm.priors
aggsumv(fitm.weights.w, ytrain)

@head fitm.T 
@head transf(model, Xtrain)
@head transf(model, Xtest)

## X-loadings matrix
## = 線形判別関数の係数
## = RパッケージMASSの関数ldaの「LD」
fitm.V
fitm.V' * fitm.V

## 重み付きPCAによって計算された説明された分散 
## 変換スケールでのクラス中心の
summary(model).explvarx

## スコア空間へのクラス中心の投影
ct = fitm.Tcenters 
f, ax = plotxy(fitm.T[:, 1], fitm.T[:, 2], ytrain; ellipse = true, title = "FDA",
    xlabel = "Score-1", ylabel = "Score-2")
scatter!(ax, ct[:, 1], ct[:, 2], marker = :star5, markersize = 15, color = :red)  # 使用可能なマーカーシンボルを参照
f
```
