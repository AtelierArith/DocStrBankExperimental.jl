```
BQCRB(x::AbstractVector, p, dp, rho, drho; b=nothing, db=nothing, LDtype=:SLD, btype=1, eps=GLOBAL_EPS)
```

ベイジアン量子クレーマー-ラオ限界（BQCRB）の計算。

  * `x`: 積分のためのパラメータのレジーム。
  * `p`: 事前分布。
  * `dp`: 推定される未知のパラメータに関する事前分布の導関数。例えば、dp[0]は最初のパラメータに関する導関数ベクトルです。
  * `rho`: パラメータ化された密度行列。
  * `drho`: 推定される未知のパラメータに関するパラメータ化された密度行列（rho）の導関数。
  * `b`: 形式 $\textbf{b}=(b(x_0),b(x_1),\dots)^{\mathrm{T}}$ のバイアスのベクトル。
  * `db`: 推定される未知のパラメータに関するbの導関数、これは $\textbf{b}'=(\partial_0 b(x_0),\partial_1 b(x_1),\dots)^{\mathrm{T}}$ の形で表現されるべきです。
  * `LDtype`: QFI（QFIM）のタイプは目的関数として設定できます。オプションは「SLD」（デフォルト）、「RLD」、「LLD」です。
  * `btype`: BCRBのタイプ。オプションは1、2、3です。
  * `eps`: マシンエプシロン。

```
