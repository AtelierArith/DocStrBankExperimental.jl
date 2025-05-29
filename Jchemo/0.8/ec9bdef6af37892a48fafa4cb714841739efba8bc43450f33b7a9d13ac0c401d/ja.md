```
dkplsr(; kwargs...)
dkplsr(X, Y; kwargs...)
dkplsr(X, Y, weights::Weight; kwargs...)
dkplsr!(X::Matrix, Y::Union{Matrix, BitMatrix}, weights::Weight; kwargs...)
```

直接カーネル部分最小二乗回帰 (DKPLSR) (Bennett & Embrechts 2003)。

  * `X` : Xデータ (n, p)。
  * `Y` : Yデータ (n, q)。
  * `weights` : 観測値の重み (n)。 `Weight` 型でなければなりません (例えば、関数 `mweight` を参照)。

キーワード引数:

  * `nlv` : 考慮すべき潜在変数 (LV) の数。
  * `kern` : グラム行列を計算するために使用されるカーネルの種類。 可能な値は: `:krbf`, `:kpol`。 それぞれの関数 `krbf` と `kpol` のキーワード引数を参照してください。
  * `scal` : ブール値。 `true` の場合、`X` と `Y` の各列はその未修正の標準偏差でスケーリングされます。

このメソッドはカーネルグラム行列を構築し、その後通常のPLSRアルゴリズムを実行します。これは「真の」KPLSR (Nipals) アルゴリズム (関数 `kplsr`) よりも速いですが、同等ではありません (Rosipal & Trejo 2001で説明)。

## 参考文献

Bennett, K.P., Embrechts, M.J., 2003. カーネル部分最小二乗回帰に関する最適化の視点, in: 学習理論の進展: 方法、モデル、応用, NATO科学シリーズIII: コンピュータおよびシステム科学. IOS Press Amsterdam, pp. 227-250.

Rosipal, R., Trejo, L.J., 2001. 再生カーネルヒルベルト空間におけるカーネル部分最小二乗回帰. 機械学習研究ジャーナル 2, 97-123.

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

nlv = 20
kern = :krbf ; gamma = 1e-1 ; scal = false
#gamma = 1e-4 ; scal = true
model = dkplsr(; nlv, kern, gamma, scal) ;
fit!(model, Xtrain, ytrain)
@names model
@names model.fitm
@head model.fitm.T

coef(model)
coef(model; nlv = 3)

@head transf(model, Xtest)
@head transf(model, Xtest; nlv = 3)

res = predict(model, Xtest)
@head res.pred
@show rmsep(res.pred, ytest)
plotxy(res.pred, ytest; color = (:red, .5), bisect = true, xlabel = "予測",  
    ylabel = "観測値").f  

####### 関数 sinc(x) のフィッティングの例
####### Rosipal & Trejo 2001 p. 105-106 で説明 
x = collect(-10:.2:10) 
x[x .== 0] .= 1e-5
n = length(x)
zy = sin.(abs.(x)) ./ abs.(x) 
y = zy + .2 * randn(n) 
nlv = 2
gamma = 1 / 3
model = dkplsr(; nlv, gamma) ;
fit!(model, x, y)
pred = predict(model, x).pred 
f, ax = scatter(x, y) 
lines!(ax, x, zy, label = "真のモデル")
lines!(ax, x, vec(pred), label = "フィッティングモデル")
axislegend("方法")
f
```
