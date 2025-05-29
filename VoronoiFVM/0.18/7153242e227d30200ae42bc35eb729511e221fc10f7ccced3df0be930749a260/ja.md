```julia
prepare_diffeq!(sys, jacval, tjac)

```

VoronoiFVMDiffEqで使用するためにシステムを準備します。

  * `jacval`: プロトタイプを取得するためにヤコビアンを評価する値
  * `tjac`: ヤコビアンの時間モーメント

ヤコビアンのプロトタイプを返します。
