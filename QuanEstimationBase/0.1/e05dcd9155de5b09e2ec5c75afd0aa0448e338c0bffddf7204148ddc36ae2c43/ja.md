```
HCRB(ρ::AbstractMatrix, dρ::AbstractVector, W::AbstractMatrix; eps=GLOBAL_EPS)
```

Holevo Cramer-Rao bound (HCRB)を半正定値計画法（SDP）を用いて計算します。

  * `ρ`: 密度行列。
  * `dρ`: 推定される未知のパラメータに対する密度行列の導関数。例えば、drho[0]は最初のパラメータに対する導関数ベクトルです。
  * `W`: 重み行列。
  * `eps`: マシンイプシロン。
