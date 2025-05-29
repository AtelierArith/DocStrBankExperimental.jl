```
varimax(A; gamma = 1.0, minit = 20, maxit = 1000, reltol = 1e-12)
```

VARIMAXは、入力行列の列ベクトルに対してvarimax（またはquartimax、equamax、parsimax）回転を実行します。

# 入力引数

  * `A::Matrix{Float64}`: 回転される列ベクトルを持つ入力行列。d, m = size(A).
  * `gamma::Float64`: デフォルトは1。gamma = 0, 1, m/2、および d(m - 1)/(d + m - 2)は、それぞれquartimax、varimax、equamax、およびparsimaxに対応します。
  * `minit::Int`: デフォルトは20。停止基準が最初に失敗した場合の最小反復回数。
  * `maxit::Int`: デフォルトは1000。最大反復回数。
  * `reltol::Float64`: デフォルトは1e-12。停止基準の相対許容誤差。

# 出力引数

  * `B::Matrix{Float64}`: すでに回転された列を持つ出力行列。

Haotian Liによって実装されました、2019年8月20日
