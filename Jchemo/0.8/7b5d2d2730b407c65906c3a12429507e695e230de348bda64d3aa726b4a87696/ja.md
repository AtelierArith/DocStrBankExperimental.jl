```
vip(object::Union{Plsr, Pcr, Splsr, Spcr}; nlv = nothing)
vip(object::Union{Plsr, Pcr, Splsr, Spcr}, Y; nlv = nothing)
```

プロジェクションにおける変数重要度 (VIP)。

  * `object` : フィッティングされたモデル。
  * `Y` : モデルをフィットさせるために使用されたYデータ。

キーワード引数:

  * `nlv` : 考慮すべき潜在変数 (LV) の数。 `nothing` の場合、最大モデルが考慮されます。

( X, Y ) に対してA個の潜在変数でフィッティングされたPLSモデル (またはPCRなど) において、変数xj (Xの列j):

  * VIP(xj) = Sum.a(1,...,A) R2(Yc, ta) waj^2 / Sum.a(1,...,A) R2(Yc, ta) (1 / p)

ここで:

  * Ycは中心化されたYです。
  * taはa番目のXスコアです。
  * R2(Yc, ta)はtaによって説明されるYcの分散の割合、すなわち ||Yc.hat||^2 / ||Yc||^2 (ここでYc.hatはtaによるYcの最小二乗推定) です。

`Y` が使用される場合、R2(Yc, ta)は冗長性Rd(Yc, ta) (関数 `rd` を参照) に置き換えられます。これはTenenhaus 1998 p.139のようになります。

## 参考文献

Chong, I.-G., Jun, C.-H., 2005. 多重共線性が存在する場合のいくつかの変数選択法の性能。Chemometrics and Intelligent Laboratory Systems 78, 103–112. https://doi.org/10.1016/j.chemolab.2004.12.011

Mehmood, T., Sæbø, S., Liland, K.H., 2020. 部分最小二乗回帰における変数選択法の比較。Journal of Chemometrics 34, e3226. https://doi.org/10.1002/cem.3226

Tenenhaus, M., 1998. PLS回帰: 理論と実践。 Editions Technip, Paris.

## 例

```julia
using Jchemo

X = [1. 2 3 4; 4 1 6 7; 12 5 6 13; 27 18 7 6 ; 12 11 28 7] 
Y = [10. 11 13; 120 131 27; 8 12 4; 1 200 8; 100 10 89] 
y = Y[:, 1] 
ycla = [1; 1; 1; 2; 2]

nlv = 3
model = plskern(; nlv)
fit!(model, X, y)
res = vip(model.fitm)
@names res
res.imp

fit!(model, X, Y)
vip(model.fitm).imp
vip(model.fitm, Y).imp

## PLSDAの場合

model = plsrda(; nlv) 
fit!(model, X, ycla)
@names model.fitm
fitm = model.fitm.fitm ;  # フィッティングされたPLSモデル
vip(fitm).imp
Ydummy = dummy(ycla).Y
vip(fitm, Ydummy).imp

model = plslda(; nlv) 
fit!(model, X, ycla)
@names model.fitm.fitm
fitm = model.fitm.fitm.embfitm ;  # フィッティングされたPLSモデル
vip(fitm).imp
vip(fitm, Ydummy).imp
```
