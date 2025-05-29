```
viperm(model, X, Y; rep = 50, psamp = .3, score = rmsep)
```

直接的な置換による変数の重要性。

  * `model` : 評価するモデル。
  * `X` : Xデータ (n, p)。
  * `Y` : Yデータ (n, q)。

キーワード引数:

  * `rep` : 分割の繰り返し回数（トレーニング/テスト）。
  * `psamp` : `score` を計算するためにテストセットとして使用されるデータの割合。
  * `score` : 予測スコアを計算する関数。

原理は次のとおりです：

  * データ (X, Y) はランダムにトレーニングセットとテストセットに分割されます。
  * モデルは Xtrain にフィットされ、スコア（誤差率）が Xtest で計算されます。これが基準誤差率を与えます。
  * Xtest の特定の変数（特徴） j の行がランダムに置換されます（Xtest の残りは変更されません）。スコアは Xtest*perm*j（すなわち、変数 j の行が置換された後の Xtest）で計算されます。変数 j の重要性は、このスコアと基準スコアの差によって計算されます。
  * このプロセスは各変数 j について個別に実行され、`rep` 回繰り返されます。出力には平均結果と各繰り返しの結果が提供されます。

一般的に、この方法はランダムフォレストで使用されるバギング置換法と同様の結果を返します（Breiman, 2001）。

## 参考文献

  * Nørgaard, L., Saudland, A., Wagner, J., Nielsen, J.V., Munck, L.,

Engelsen, S.B., 2000. インターバル部分最小二乗回帰 (iPLS): 近赤外分光法からの例を用いた比較化学計算研究。Appl Spectrosc 54, 413–419.  https://doi.org/10.1366/0003702001949500

## 例

```julia
using Jchemo, JchemoData, JLD2, CairoMakie
mypath = dirname(dirname(pathof(JchemoData)))
db = joinpath(mypath, "data", "tecator.jld2") 
@load db dat
@names dat
X = dat.X
Y = dat.Y 
wl_str = names(X)
wl = parse.(Float64, wl_str) 
ntot, p = size(X)
typ = Y.typ
namy = names(Y)[1:3]
plotsp(X, wl; xlabel = "波長 (nm)", ylabel = "吸光度").f
s = typ .== "train"
Xtrain = X[s, :]
Ytrain = Y[s, namy]
Xtest = rmrow(X, s)
Ytest = rmrow(Y[:, namy], s)
ntrain = nro(Xtrain)
ntest = nro(Xtest)
ntot = ntrain + ntest
(ntot = ntot, ntrain, ntest)

## j 番目の y 変数で作業する 
j = 2
nam = namy[j]
ytrain = Ytrain[:, nam]
ytest = Ytest[:, nam]

model = plskern(nlv = 9)
res = viperm(model, Xtrain, ytrain; rep = 50, score = rmsep) ;
z = vec(res.imp)
f = Figure(size = (500, 400))
ax = Axis(f[1, 1]; xlabel = "波長 (nm)", ylabel = "重要性")
scatter!(ax, wl, vec(z); color = (:red, .5))
u = [910; 950]
vlines!(ax, u; color = :grey, linewidth = 1)
f

model = rfr(n_trees = 10, max_depth = 2000, min_samples_leaf = 5)
res = viperm(model, Xtrain, ytrain; rep = 50)
z = vec(res.imp)
f = Figure(size = (500, 400))
ax = Axis(f[1, 1];
    xlabel = "波長 (nm)", 
    ylabel = "重要性")
scatter!(ax, wl, vec(z); color = (:red, .5))
u = [910; 950]
vlines!(ax, u; color = :grey, linewidth = 1)
f
```
