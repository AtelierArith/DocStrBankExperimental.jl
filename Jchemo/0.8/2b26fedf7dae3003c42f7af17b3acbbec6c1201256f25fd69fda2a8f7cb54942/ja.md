```
svmda(; kwargs...)
svmda(X, y; kwargs...)
```

識別のためのサポートベクターマシン "C-SVC" (SVM-DA)。

  * `X` : Xデータ (n, p)。
  * `y` : 単変量クラスメンバーシップ (n)。

キーワード引数:

  * `kern` : グラム行列を計算するために使用されるカーネルのタイプ。可能な値は: `:krbf`, `:kpol`, `:klin`, `:ktanh`。以下を参照。
  * `gamma` : `kern` パラメータ、以下を参照。
  * `degree` : `kern` パラメータ、以下を参照。
  * `coef0` : `kern` パラメータ、以下を参照。
  * `cost` : 制約違反のコスト C パラメータ。
  * `epsilon` : 損失関数におけるエプシロンパラメータ。
  * `scal` : ブール値。`true` の場合、`X` の各列はその未修正の標準偏差でスケーリングされる。

カーネルタイプ:

  * :krbf – 放射基底関数: exp(-gamma * ||x - y||^2)
  * :kpol – 多項式: (gamma * x' * y + coef0)^degree
  * :klin – 線形: x' * y
  * :ktan – シグモイド: tanh(gamma * x' * y + coef0)

この関数は、LIBSVM.jl (https://github.com/JuliaML/LIBSVM.jl) を使用しており、これはライブラリ LIBSVM (Chang & Li 2001) へのインターフェースです。

## 参考文献

Juliaパッケージ LIBSVM.jl: https://github.com/JuliaML/LIBSVM.jl

Chang, C.-C. & Lin, C.-J. (2001). LIBSVM: サポートベクターマシンのためのライブラリ。ソフトウェアは http://www.csie.ntu.edu.tw/~cjlin/libsvm で入手可能。詳細なドキュメント (アルゴリズム、公式、...) は http://www.csie.ntu.edu.tw/~cjlin/papers/libsvm.ps.gz で見つけることができます。

Chih-Chung Chang と Chih-Jen Lin, LIBSVM: サポートベクターマシンのためのライブラリ。ACM Transactions on Intelligent Systems and Technology, 2:27:1–27:27, 2011。ソフトウェアは http://www.csie.ntu.edu.tw/~cjlin/libsvm で入手可能。

Schölkopf, B., Smola, A.J., 2002. カーネルを用いた学習: サポートベクターマシン、正則化、最適化、そしてそれを超えて。適応計算と機械学習。MIT Press, ケンブリッジ, マサチューセッツ。

## 例

```julia
using Jchemo, JchemoData, JLD2
path_jdat = dirname(dirname(pathof(JchemoData)))
db = joinpath(path_jdat, "data/forages2.jld2")
@load db dat
@names dat
X = dat.X
Y = dat.Y
n = nro(X) 
s = Bool.(Y.test)
Xtrain = rmrow(X, s)
ytrain = rmrow(Y.typ, s)
Xtest = X[s, :]
ytest = Y.typ[s]
ntrain = nro(Xtrain)
ntest = nro(Xtest)
(ntot = n, ntrain, ntest)
tab(ytrain)
tab(ytest)

kern = :krbf ; gamma = 1e4
cost = 1000 ; epsilon = .5
model = svmda(; kern, gamma, cost, epsilon) 
fit!(model, Xtrain, ytrain)
@names model
@names model.fitm
fitm = model.fitm ;
fitm.lev
fitm.ni

res = predict(model, Xtest) ; 
@names res 
@head res.pred
errp(res.pred, ytest)
conf(res.pred, ytest).cnt
```
