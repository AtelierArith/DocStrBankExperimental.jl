```
blockscal(; kwargs...)
blockscal(Xbl; kwargs...)
blockscal(Xbl, weights::Weight; kwargs...)
```

マルチブロックXデータをスケーリングします。

  * `Xbl` : Xデータのブロックのリスト（行列のベクトル）    通常、（n, p）データの関数`mblock`の出力です。
  * `weights` : 観測値（ブロックの行）の重み（n）。    `Weight`型でなければなりません（例えば、関数`mweight`を参照）。

キーワード引数：

  * `centr` : ブール値。`true`の場合、`Xbl`のブロックの各列が    中心化されます（ブロックスケーリングの前に）。
  * `scal` : ブール値。`true`の場合、`Xbl`のブロックの各列が    補正されていない標準偏差でスケーリングされます    （ブロックスケーリングの前に）。
  * `bscal` : ブロックスケーリングのタイプ。可能な値は：   `:none`, `:frob`, `:mfa`, `:ncol`, `:sd`。以下を参照してください。

実装されている場合、データ変換は次の順序で行われます：列の中心化、列のスケーリング、そして最後にブロックスケーリング。

ブロックスケーリングのタイプ：

  * `:none` : ブロックスケーリングなし。
  * `:frob` : Dをベクトル`weights.w`の対角行列とします。    各ブロックXはそのフロベニウスノルムで割られます  = sqrt(tr(X' * D * X))。    このスケーリングの後、tr(X' * D * X) = 1。
  * `:mfa` : 各ブロックXはsvで割られます。ここでsvはXの主成分    特異値です（これは「MFA」アプローチです；フランス語で「AFM」）。
  * `:ncol` : 各ブロックXはブロックの列数で割られます。
  * `:sd` : 各ブロックXは（ブロック列の加重分散の合計）の平方根で割られます。    このスケーリングの後、加重分散の合計 = 1。

## 例

```julia
using Jchemo
n = 5 ; m = 3 ; p = 10 
X = rand(n, p) 
Xnew = rand(m, p)
listbl = [3:4, 1, [6; 8:10]]
Xbl = mblock(X, listbl) 
Xblnew = mblock(Xnew, listbl) 
@head Xbl[3]

centr = true ; scal = true
bscal = :frob
model = blockscal(; centr, scal, bscal)
fit!(model, Xbl)
## データ変換
zXbl = transf(model, Xbl) ; 
@head zXbl[3]

zXblnew = transf(model, Xblnew) ; 
zXblnew[3]
```
