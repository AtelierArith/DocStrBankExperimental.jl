```
isel!(model, X, Y, wl = 1:nco(X); rep = 1, nint = 5, psamp = .3, score = rmsep)
```

区間変数選択。

  * `model` : 評価するモデル。
  * `X` : Xデータ (n, p)。
  * `Y` : Yデータ (n, q)。
  * `wl` : X列のオプションの数値ラベル (p, 1)。

キーワード引数:  

  * `rep` : 分割の繰り返し回数（トレーニング/テスト）。
  * `nint` : 区間の数。
  * `psamp` : `score`を計算するためにテストセットとして使用されるデータの割合。
  * `score` : 予測スコアを計算する関数。

原則は次のとおりです：

  * データ (X, Y) はランダムにトレーニングセットとテストセットに分割されます。
  * `X` の範囲 1:p は、可能な場合は等しいサイズの `nint` 区間に分割されます。
  * モデルはトレーニングセットにフィットされ、スコア（誤差率）は、最初にすべての p 変数（参照）を考慮し、次に各 `nint` 区間についてテストセットで計算されます。
  * このプロセスは `rep` 回繰り返されます。平均結果は出力に提供され、各繰り返しの結果も提供されます。

## 参考文献

  * Nørgaard, L., Saudland, A., Wagner, J., Nielsen, J.V., Munck, L.,

Engelsen, S.B., 2000. 区間部分最小二乗回帰 (iPLS): 近赤外分光法の例を用いた比較化学計算研究。Appl Spectrosc 54, 413–419.  https://doi.org/10.1366/0003702001949500

## 例

```julia
using Jchemo, JchemoData, DataFrames, JLD2, CairoMakie
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

## j番目のy変数で作業する 
j = 2
nam = namy[j]
ytrain = Ytrain[:, nam]
ytest = Ytest[:, nam]

model = plskern(nlv = 5)
nint = 10
res = isel!(model, Xtrain, ytrain, wl; rep = 30, nint) ;
res.res_rep
res.res0_rep
zres = res.res
zres0 = res.res0
f = Figure(size = (650, 300))
ax = Axis(f[1, 1], xlabel = "波長 (nm)", ylabel = "RMSEP_Val",
    xticks = zres.lo)
scatter!(ax, zres.mid, zres.y1; color = (:red, .5))
vlines!(ax, zres.lo; color = :grey, linestyle = :dash, linewidth = 1)
hlines!(ax, zres0.y1, linestyle = :dash)
f
```
