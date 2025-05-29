```
svmr(; kwargs...)
svmr(X, y; kwargs...)
```

回帰のためのサポートベクターマシン（Epsilon-SVR）。

  * `X` : Xデータ (n, p)。
  * `y` : 単変量yデータ (n)。

キーワード引数：

  * `kern` : グラム行列を計算するために使用されるカーネルのタイプ。可能な値は： `:krbf`, `:kpol`, `:klin`, `:ktan`。以下を参照。
  * `gamma` : `kern` パラメータ、以下を参照。
  * `coef0` : `kern` パラメータ、以下を参照。
  * `degree` : `kern` パラメータ、以下を参照。
  * `cost` : 制約違反のCパラメータのコスト。
  * `epsilon` : 損失関数におけるエプシロンパラメータ。
  * `scal` : ブール値。`true` の場合、`X` の各列はその未修正の標準偏差でスケーリングされる。

カーネルタイプ：

  * :krbf – 放射基底関数：exp(-gamma * ||x - y||^2)
  * :kpol – 多項式：(gamma * x' * y + coef0)^degree
  * :klin – 線形：x' * y
  * :ktan – シグモイド：tanh(gamma * x' * y + coef0)

この関数は、LIBSVM.jl (https://github.com/JuliaML/LIBSVM.jl) を使用しており、これはLIBSVMライブラリ（Chang & Li 2001）へのインターフェースです。

## 参考文献

JuliaパッケージLIBSVM.jl: https://github.com/JuliaML/LIBSVM.jl

Chang, C.-C. & Lin, C.-J. (2001). LIBSVM: サポートベクターマシンのためのライブラリ。ソフトウェアは http://www.csie.ntu.edu.tw/~cjlin/libsvm で入手可能。詳細なドキュメント（アルゴリズム、公式など）は http://www.csie.ntu.edu.tw/~cjlin/papers/libsvm.ps.gz で見つけることができます。

Chih-Chung Chang と Chih-Jen Lin, LIBSVM: サポートベクターマシンのためのライブラリ。ACM Transactions on Intelligent Systems and Technology, 2:27:1–27:27, 2011。ソフトウェアは http://www.csie.ntu.edu.tw/~cjlin/libsvm で入手可能。

Schölkopf, B., Smola, A.J., 2002. カーネルを用いた学習：サポートベクターマシン、正則化、最適化、そしてそれを超えて。適応計算と機械学習。MIT Press, ケンブリッジ, マサチューセッツ。

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
p = nco(X)

kern = :krbf ; gamma = .1
cost = 1000 ; epsilon = 1
model = svmr(; kern, gamma, cost, epsilon) 
fit!(model, Xtrain, ytrain)
@names model
@names model.fitm

res = predict(model, Xtest)
@head res.pred
@show rmsep(res.pred, ytest)
plotxy(res.pred, ytest; color = (:red, .5), bisect = true, xlabel = "予測", 
    ylabel = "観測").f    

####### sinc(x) 関数のフィッティングの例
####### Rosipal & Trejo 2001 p. 105-106 に記載
x = collect(-10:.2:10) 
x[x .== 0] .= 1e-5
n = length(x)
zy = sin.(abs.(x)) ./ abs.(x) 
y = zy + .2 * randn(n) 
kern = :krbf ; gamma = .1
model = svmr(; kern, gamma) 
fit!(model, x, y)
pred = predict(model, x).pred 
f, ax = scatter(x, y) 
lines!(ax, x, zy, label = "真のモデル")
lines!(ax, x, vec(pred), label = "フィッティングモデル")
axislegend("方法")
f
```
