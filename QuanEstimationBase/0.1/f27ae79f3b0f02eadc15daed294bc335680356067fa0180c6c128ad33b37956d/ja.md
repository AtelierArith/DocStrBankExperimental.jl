```
NHB(ρ::AbstractMatrix, dρ::AbstractVector, W::AbstractMatrix)
```

ナガオカ-ハヤシ境界 (NHB) を半正定値計画 (SDP) を通じて。

  * `ρ`: 密度行列。
  * `dρ`: 推定される未知のパラメータに関する密度行列の導関数。例えば、drho[0] は最初のパラメータに関する導関数ベクトルです。
  * `W`: 重み行列。
