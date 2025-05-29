```
QFIM(ρ::Matrix{T}, dρ::Matrix{T}; LDtype=:SLD, exportLD::Bool= false, eps=GLOBAL_EPS) where {T<:Complex}
```

量子フィッシャー情報（QFI）の計算、すべてのタイプに対して。

  * `ρ`: 密度行列。
  * `dρ`: 推定される未知のパラメータに関する密度行列の導関数。例えば、drho[1]は最初のパラメータに関する導関数ベクトルです。
  * `LDtype`: QFI（QFIM）のタイプは目的関数として設定できます。オプションは `:SLD`（デフォルト）、`:RLD`、および `:LLD` です。
  * `exportLD`: Fとは別に対数導関数をエクスポートします。
  * `eps`: マシンイプシロン。
