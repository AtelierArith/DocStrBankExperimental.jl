```
krr(; kwargs...)
krr(X, Y; kwargs...)
krr(X, Y, weights::Weight; kwargs...)
krr!(X::Matrix, Y::Union{Matrix, BitMatrix}, weights::Weight; kwargs...)
```

SVD因子分解によって実装されたカーネルリッジ回帰（KRR）。

  * `X` : Xデータ (n, p)。
  * `Y` : Yデータ (n, q)。
  * `weights` : 観測値の重み (n)。 `Weight` 型でなければなりません（例えば、関数 `mweight` を参照）。

キーワード引数：

  * `lb` : リッジ正則化パラメータ "lambda"。
  * `kern` : グラム行列を計算するために使用されるカーネルのタイプ。可能な値は `:krbf`, `:kpol` です。それぞれの関数 `krbf` と `kpol` のキーワード引数を参照してください。
  * `scal` : ブール値。 `true` の場合、`X` の各列はその未修正の標準偏差でスケーリングされます。

KRRは最小二乗SVM回帰（LS-SVMR）とも呼ばれます。この手法は、観測値を除外するマージがないSVM回帰の特定のケースに近いです（エプシロン係数がゼロに設定されています）。違いは、SVMのL1の代わりにL2ノルム最適化が行われることです。

## 参考文献

Bennett, K.V., Embrechts, M.J., 2003. カーネル部分最小二乗回帰に関する最適化の視点, in: 学習理論の進展: 方法、モデル、応用, NATO科学シリーズIII: コンピュータ＆システム科学。IOS Press Amsterdam, pp. 227-250.

Cawley, G.C., Talbot, N.L.C., 2002. 縮小ランクカーネルリッジ回帰。Neural Processing Letters 16, 293-302.  https://doi.org/10.1023/A:1021798002258

Krell, M.M., 2018. サポートベクターマシン分類の一般化、デコーディング、および最適化。arXiv:1801.04929.

Saunders, C., Gammerman, A., Vovk, V., 1998. 双対変数におけるリッジ回帰学習アルゴリズム, in: 第15回国際機械学習会議の議事録。Morgan Kaufitmann, pp. 515-521.

Suykens, J.A.K., Lukas, L., Vandewalle, J., 2000. 最小二乗サポートベクターマシンを用いたスパース近似。2000 IEEE国際回路およびシステムシンポジウム。21世紀の新興技術。議事録 (IEEE Cat No.00CH36353)。 https://doi.org/10.1109/ISCAS.2000.856439

Welling, M., n.d. カーネルリッジ回帰。トロント大学コンピュータサイエンス学部、カナダ、トロント。 https://www.ics.uci.edu/~welling/classnotes/papers_class/Kernel-Ridge.pdf

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

lb = 1e-3
kern = :krbf ; gamma = 1e-1
model = krr(; lb, kern, gamma) ;
fit!(model, Xtrain, ytrain)
@names model
@names model.fitm

coef(model)

res = predict(model, Xtest)
@head res.pred
@show rmsep(res.pred, ytest)
plotxy(res.pred, ytest; color = (:red, .5), bisect = true, xlabel = "予測", 
   ylabel = "観測").f    

coef(model; lb = 1e-1)
res = predict(model, Xtest; lb = [.1 ; .01])
@head res.pred[1]
@head res.pred[2]

lb = 1e-3
kern = :kpol ; degree = 1
model = krr(; lb, kern, degree) 
fit!(model, Xtrain, ytrain)
res = predict(model, Xtest)
rmsep(res.pred, ytest)

####### 関数sinc(x)のフィッティングの例
####### Rosipal & Trejo 2001 p. 105-106に記載
x = collect(-10:.2:10) 
x[x .== 0] .= 1e-5
n = length(x)
zy = sin.(abs.(x)) ./ abs.(x) 
y = zy + .2 * randn(n) 
lb = 1e-1
kern = :krbf ; gamma = 1 / 3
model = krr(; lb, kern, gamma) 
fit!(model, x, y)
pred = predict(model, x).pred 
f, ax = scatter(x, y) 
lines!(ax, x, zy, label = "真のモデル")
lines!(ax, x, vec(pred), label = "フィッティングモデル")
axislegend("方法")
f
```
