```
sampwsp(X, dmin; recod = false, maxit = nro(X))
```

WSPサンプリングによるトレーニングセットとテストセットの構築。  

  * `X` : Xデータ (n, p)。
  * `dmin` : 距離 "dmin" (Santiago et al. 2012)。

キーワード引数: 

  * `recod` : サンプリング前に `X` が再コーディングされるかどうかを示すブール値（下記参照）。
  * `maxit` : 最大反復回数。

2つの出力（データの行インデックス）が返されます: 

  * `train` (`n` - k),
  * `test` (k)。

出力 `test` は "Wootton, Sergent, Phan-Tan-Luu" (WSP) アルゴリズムから構築され、`X` ドメイン内で均等に分布したサンプルを生成することが想定されています (Santiago et al. 2012)。

`recod = true` の場合、`X` の各列 x は [0, 1] の範囲に再コーディングされ、ドメインの中心はベクトル `repeat([.5], p)` です。列 x は次のように再コーディングされます: 

  * vmin = 最小値(x)
  * vmax = 最大値(x)
  * vdiff = vmax - vmin
  * x .=  0.5 .+ (x .- (vdiff / 2 + vmin)) / vdiff

## 参考文献

Béal A. 2015. Description et sélection de données en grande dimensio. Thèse de doctorat. Laboratoire d’Instrumentation et de sciences analytiques, Ecole doctorale des siences chimiques, Université d'Aix-Marseille.

Santiago, J., Claeys-Bruno, M., Sergent, M., 2012. Construction of space-filling  designs using WSP algorithm for high dimensional spaces.  Chemometrics and Intelligent Laboratory Systems, Selected Papers from  Chimiométrie 2010 113, 26–31. https://doi.org/10.1016/j.chemolab.2011.06.003

## 例

```julia
using Jchemo

n = 600 ; p = 2
X = rand(n, p)
dmin = .5
s = sampwsp(X, dmin)
@names res
@show length(s.test)
plotxy(X[s.test, 1], X[s.test, 2]).f
```
