```
nipalsmiss(X; kwargs...)
nipalsmiss(X, UUt, VVt; kwargs...)
```

欠損データを持つ行列の最初のスコアとローディングベクトルを計算するためのNipals。

  * `X` : Xデータ (n, p)。
  * `UUt` : グラム・シュミット直交化のための行列 (n, n)。
  * `VVt` : グラム・シュミット直交化のための行列 (p, p)。

キーワード引数:

  * `tol` : 反復を停止するための許容値。
  * `maxit` : 最大反復回数。

関数 `nipals` を参照してください。

## 参考文献

K.R. Gabriel, S. Zamir, 重みの任意の選択による最小二乗法による行列の低ランク近似, Technometrics 21 (1979) 489–498.

Wright, K., 2018. パッケージ nipals: グラム・シュミット直交化を用いた主成分分析. https://cran.r-project.org/

## 例

```julia
using Jchemo 

X = [1. 2 missing 4 ; 4 missing 6 7 ; 
    missing 5 6 13 ; missing 18 7 6 ; 
    12 missing 28 7] 

res = nipalsmiss(X)
res.niter
res.sv
res.v
res.u
```
