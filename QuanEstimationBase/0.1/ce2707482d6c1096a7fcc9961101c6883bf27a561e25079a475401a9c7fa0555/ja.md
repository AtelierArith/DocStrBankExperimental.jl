```
QFIM_Kraus(ρ0::AbstractMatrix, K::AbstractVector, dK::AbstractVector; LDtype=:SLD, exportLD::Bool=false, eps=GLOBAL_EPS)
```

クアンタムフィッシャー情報（QFI）およびクアンタムフィッシャー情報行列（QFIM）をクラウス演算子を用いて計算します。

  * `ρ0`: 密度行列。
  * `K`: クラウス演算子。
  * `dK`: 推定される未知のパラメータに対するクラウス演算子の導関数。例えば、dK[0]は最初のパラメータに対する導関数ベクトルです。
  * `LDtype`: QFI（QFIM）のタイプを目的関数として設定できます。オプションは `:SLD`（デフォルト）、`:RLD` および `:LLD` です。
  * `exportLD`: 対数導関数の値をエクスポートするかどうか。Trueに設定すると、対数導関数の値がエクスポートされます。
  * `eps`: マシンエプシロン。
