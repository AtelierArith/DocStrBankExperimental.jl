```
nipals(X; kwargs...)
nipals(X, UUt, VVt; kwargs...)
```

行列の最初のスコアとローディングベクトルを計算するためのNipals。

  * `X` : Xデータ (n, p)。
  * `UUt` : グラム・シュミット直交化のための行列 (n, n)。
  * `VVt` : グラム・シュミット直交化のための行列 (p, p)。

キーワード引数：

  * `tol` : 反復を停止するための許容値。
  * `maxit` : 最大反復回数。

この関数は次を見つけます：

  * {u, v, sv} = argmin(||X - u * sv * v'||)

制約条件：

  * ||u|| = ||v|| = 1

交互最小二乗法を使用してSVDを計算します (Gabriel & Zalir 1979)。

最終的に、X ~ u * sv * v' となり、ここで：

  * u : 左特異ベクトル (u * sv = スコア)
  * v : 右特異ベクトル (ローディング)
  * sv : 特異値。

NIPALSが逐次的に脱落した行列に使用されると、ベクトルuとvは丸め誤差の蓄積により直交性を失う可能性があります。直交性はグラム・シュミット法 (引数 `UUt` と `VVt`) から再構築できます。

## 参考文献

K.R. Gabriel, S. Zamir, Lower rank approximation of matrices by least squares with any choice of weights,  Technometrics 21 (1979) 489–498.

## 例

```julia
using Jchemo, LinearAlgebra

X = rand(5, 3)

res = nipals(X)
res.niter
res.sv
svd(X).S[1] 
res.v
svd(X).V[:, 1] 
res.u
svd(X).U[:, 1] 
```
