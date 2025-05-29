```
plscan(; kwargs...)
plscan(X, Y; kwargs...)
plscan(X, Y, weights::Weight; kwargs...)
plscan!(X::Matrix, Y::Matrix, weights::Weight; kwargs...)
```

標準的部分最小二乗回帰（Canonical PLS）。

  * `X` : 最初のデータブロック。
  * `Y` : 2番目のデータブロック。
  * `weights` : 観測値の重み（n）。`Weight`型でなければなりません（例えば、関数`mweight`を参照）。

キーワード引数：

  * `nlv` : 計算する潜在変数（LVs = スコア）の数。
  * `bscal` : ブロックスケーリングのタイプ。可能な値は： `:none`, `:frob`。関数`blockscal`を参照。
  * `scal` : ブール値。`true`の場合、ブロック`X`および`Y`の各列は、その未修正の標準偏差でスケーリングされます（ブロックスケーリングの前に）。

Nipalsアルゴリズムを用いた標準的PLS（Wold 1984, Tenenhaus 1998 chap.11）は、Wegelin 2000でPLS-W2A（すなわちWold PLSモードA）と呼ばれています。2つのブロック`X`と`Y`は対称的な役割を果たします。スコア計算の各ステップの後、XとYはそれぞれxスコアとyスコアによってデフレートされます。

関数`summary`は以下を返します：

  * `cortx2ty`: X-LVとY-LVの間の相関。

ブロック`X`については：

  * `explvarx` : ブロックの慣性（平方フロベニウスノルム）に対するブロックLV（`Tx`）によって説明される割合。
  * `rvx2tx` : ブロックとブロックLV間のRV係数。
  * `rdx2tx` : ブロックとブロックLV間のRd係数。
  * `corx2tx` : ブロック変数とブロックLV間の相関。

ブロック`Y`についても同様の情報が返されます。

## 参考文献

Tenenhaus, M., 1998. La régression PLS: théorie et pratique. Editions Technip, Paris.

Wegelin, J.A., 2000. A Survey of Partial Least Squares (PLS) Methods, with Emphasis on  the Two-Block Case (No. 371). University of Washington, Seattle, Washington, USA.

Wold, S., Ruhe, A., Wold, H., Dunn, III, W.J., 1984. The Collinearity Problem in Linear  Regression. The Partial Least Squares (PLS) Approach to Generalized Inverses.  SIAM Journal on Scientific and Statistical Computing 5, 735–743. https://doi.org/10.1137/0905052

## 例

```julia
using Jchemo, JchemoData, JLD2
mypath = dirname(dirname(pathof(JchemoData)))
db = joinpath(mypath, "data", "linnerud.jld2") 
@load db dat
@names dat
X = dat.X
Y = dat.Y
n, p = size(X)
q = nco(Y)

nlv = 2
bscal = :frob
model = plscan(; nlv, bscal)
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
