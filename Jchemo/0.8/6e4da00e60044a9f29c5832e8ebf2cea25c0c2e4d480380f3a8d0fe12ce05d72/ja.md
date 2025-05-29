```
rr(; kwargs...)
rr(X, Y; kwargs...)
rr(X, Y, weights::Weight; kwargs...)
rr!(X::Matrix, Y::Union{Matrix, BitMatrix}, weights::Weight; kwargs...)
```

リッジ回帰 (RR) は SVD 分解によって実装されています。

  * `X` : Xデータ (n, p)。
  * `Y` : Yデータ (n, q)。
  * `weights` : 観測値の重み (n)。 `Weight` 型でなければなりません (例えば、関数 `mweight` を参照)。

キーワード引数:

  * `lb` : リッジ正則化パラメータ "lambda"。
  * `scal` : ブール値。 `true` の場合、`X` の各列はその未修正の標準偏差でスケーリングされます。

## 参考文献

Cule, E., De Iorio, M., 2012. リッジ回帰におけるリッジパラメータの選択をガイドする半自動的手法。 arXiv:1205.0686。

Hastie, T., Tibshirani, R., 2004. 表現配列のための効率的な二次正則化。 Biostatistics 5, 329-340.  https://doi.org/10.1093/biostatistics/kxh010

Hastie, T., Tibshirani, R., Friedman, J., 2009. 統計学習の要素: データマイニング、推論、予測, 第2版。 Springer, New York。

Hoerl, A.E., Kennard, R.W., 1970. リッジ回帰: 非直交問題のためのバイアス推定。 Technometrics 12, 55-67.  https://doi.org/10.1080/00401706.1970.10488634

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
model = rr(; lb) 
#model = rrchol(; lb) 
fit!(model, Xtrain, ytrain)
@names model
@names model.fitm

coef(model)

res = predict(model, Xtest)
@head res.pred
@show rmsep(res.pred, ytest)
plotxy(res.pred, ytest; color = (:red, .5), bisect = true, xlabel = "予測", 
    ylabel = "観測値").f    

## !! 関数 'rr' のみ ( 'rrchol' ではない)
coef(model; lb = 1e-1)
res = predict(model, Xtest; lb = [.1 ; .01])
@head res.pred[1]
@head res.pred[2]
```
