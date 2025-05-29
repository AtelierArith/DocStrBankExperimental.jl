```
plstuck(; kwargs...)
plstuck(X, Y; kwargs...)
plstuck(X, Y, weights::Weight; kwargs...)
plstuck!(X::Matrix, Y::Matrix, weights::Weight; kwargs...)
```

タッカーのインターバッテリー法による因子分析

  * `X` : 最初のデータブロック。
  * `Y` : 2番目のデータブロック。
  * `weights` : 観測値の重み (n)。タイプ `Weight` でなければなりません (例: 関数 `mweight` を参照)。

キーワード引数:

  * `nlv` : 計算する潜在変数 (LVs = スコア) の数。
  * `bscal` : ブロックスケーリングのタイプ。可能な値は: `:none`, `:frob`。関数 `blockscal` を参照。
  * `scal` : ブール値。`true` の場合、ブロック `X` と `Y` の各列は、その未修正の標準偏差でスケーリングされます (ブロックスケーリングの前に)。

インターバッテリー法による因子分析 (タッカー 1958, テネハウス 1998 第3章)。2つのブロック `X` と `Y` は対称的な役割を果たします。この方法は、ウェゲリン 2000 で PLS-SVD と呼ばれています。この方法は、SVD によって共分散行列 X'Y を因子分解します。

`summary` 出力の詳細については、関数 `plscan` を参照してください。

## 参考文献

テネハウス, M., 1998. La régression PLS: théorie et pratique. Editions Technip, パリ。

ティシュラー, A., リポヴェツキー, S., 2000. Robust canonical analysis によるモデリングと予測: 方法と応用。Computers & Operations Research 27, 217–232.  https://doi.org/10.1016/S0305-0548(99)00014-3

タッカー, L.R., 1958. An inter-battery method of factor analysis. Psychometrika 23, 111–136. https://doi.org/10.1007/BF02289009

ウェゲリン, J.A., 2000. A Survey of Partial Least Squares (PLS) Methods, with Emphasis on the Two-Block Case (No. 371). ワシントン大学, シアトル, ワシントン, USA.

## 例

```julia
using Jchemo, JchemoData, JLD2
path_jdat = dirname(dirname(pathof(JchemoData)))
db = joinpath(path_jdat, "data/linnerud.jld2") 
@load db dat
@names dat
X = dat.X 
Y = dat.Y

model = plstuck(nlv = 3)
fit!(model, X, Y) 
@names model
@names model.fitm

fitm = model.fitm
@head fitm.Tx
@head transfbl(model, X, Y).Tx

@head fitm.Ty
@head transfbl(model, X, Y).Ty

res = summary(model, X, Y) ;
@names res
res.explvarx
res.explvary
res.cortx2ty
res.rvx2tx
res.rvy2ty
res.rdx2tx
res.rdy2ty
res.corx2tx 
res.cory2ty 
```
