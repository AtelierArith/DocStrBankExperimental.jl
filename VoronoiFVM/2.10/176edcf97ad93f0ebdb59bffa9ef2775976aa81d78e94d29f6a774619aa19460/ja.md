```julia
prepare_diffeq!(state, jacval, tjac)

```

VoronoiFVMDiffEqで使用するためのシステムを準備します。

  * `jacval`: プロトタイプを取得するためにヤコビアンを評価する値
  * `tjac`: ヤコビアンの時間モーメント

ヤコビアンのプロトタイプを返します。
