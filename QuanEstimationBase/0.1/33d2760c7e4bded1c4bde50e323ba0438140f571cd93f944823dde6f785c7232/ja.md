```
BCRB(x::AbstractVector, p, dp, rho, drho; M=nothing, b=nothing, db=nothing, btype=1, eps=GLOBAL_EPS)
```

ベイズ・クレーマー・ラオ限界（BCRB）の計算。

  * `x`: 積分のためのパラメータのレジーム。
  * `p`: 事前分布。
  * `dp`: 推定される未知のパラメータに関する事前分布の導関数。例えば、dp[0]は最初のパラメータに関する導関数ベクトルです。
  * `rho`: パラメータ化された密度行列。
  * `drho`: 推定される未知のパラメータに関するパラメータ化された密度行列（rho）の導関数。
  * `M`: 正の作用素値測度（POVM）の集合。デフォルトの測定は、ランク1の対称情報完全POVM（SIC-POVM）の集合です。
  * `b`: $\textbf{b}=(b(x_0),b(x_1),\dots)^{\mathrm{T}}$の形のバイアスのベクトル。
  * `db`: 推定される未知のパラメータに関するbの導関数で、$\textbf{b}'=(\partial_0 b(x_0),\partial_1 b(x_1),\dots)^{\mathrm{T}}$の形で表現されるべきです。
  * `btype`: BCRBのタイプ。オプションは1、2、3です。
  * `eps`: マシンイプシロン。
