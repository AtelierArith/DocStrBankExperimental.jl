```
pcanipalsmiss(; kwargs...)
pcanipals(X; kwargs...)
pcanipals(X, weights::Weight; kwargs...)
pcanipals!(X::Matrix, weights::Weight; kwargs...)
```

欠損データを許容するNIPALSアルゴリズムによるPCA。

  * `X` : Xデータ (n, p)。
  * `weights` : 観測値の重み (n)。`Weight`型でなければなりません（例えば、関数`mweight`を参照）。

キーワード引数:

  * `nlv` : 主成分 (PC) の数。
  * `gs` : ブール値。`true`の場合（デフォルト）、各Xのデフレーションの前にスコアとローディングのグラム・シュミット直交化が行われます。
  * `tol` : 反復を停止するための許容値。
  * `maxit` : 最大反復回数。
  * `scal` : ブール値。`true`の場合、`X`の各列はその未修正の標準偏差でスケーリングされます。

## 参考文献

Wright, K., 2018. パッケージ nipals: グラム・シュミット直交化を用いたNIPALSによる主成分分析。 https://cran.r-project.org/

## 例

```julia
X = [1 2. missing 4 ; 4 missing 6 7 ; 
    missing 5 6 13 ; missing 18 7 6 ; 
    12 missing 28 7] 

nlv = 3 
tol = 1e-15
scal = false
#scal = true
gs = false
#gs = true
model = pcanipalsmiss(; nlv, tol, gs, maxit = 500, scal)
fit!(model, X)
@names model 
@names model.fitm
fitm = model.fitm ;
fitm.niter
fitm.sv
fitm.V
fitm.T
## 直交性 
## gs = true の場合のみ
fitm.T' * fitm.T
fitm.V' * fitm.V

## Xの欠損データを補完
model = pcanipalsmiss(; nlv = 2, gs = true) ;
fit!(model, X)
Xfit = xfit(model.fitm)
s = ismissing.(X)
X_imp = copy(X)
X_imp[s] .= Xfit[s]
X_imp
```
