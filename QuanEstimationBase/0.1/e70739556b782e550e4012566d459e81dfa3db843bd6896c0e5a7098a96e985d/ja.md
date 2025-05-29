```
CFIM(ρ::Matrix{T}, dρ::Vector{Matrix{T}}, M; eps=GLOBAL_EPS) where {T<:Complex}
```

古典フィッシャー情報行列 (CFIM) を計算します。

  * `ρ`: 密度行列。
  * `dρ`: 推定される未知のパラメータに関する密度行列の導関数。例えば、drho[1] は最初のパラメータに関する導関数ベクトルです。
  * `M`: 正の作用素値測度 (POVM) の集合。デフォルトの測定は、ランク1の対称情報完全POVM (SIC-POVM) の集合です。
  * `eps`: マシンイプシロン。
