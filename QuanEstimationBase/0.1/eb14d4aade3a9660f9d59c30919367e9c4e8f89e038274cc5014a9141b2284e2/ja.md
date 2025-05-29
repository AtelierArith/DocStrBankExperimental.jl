```
RLD(ρ::Matrix{T}, dρ::Vector{Matrix{T}}; rep="original", eps=GLOBAL_EPS) where {T<:Complex}
```

右対数微分（RLD）を計算します。RLD演算子は $\partial_{a}\rho=\rho \mathcal{R}_a$ と定義され、ここで $\rho$ はパラメータ化された密度行列です。

  * `ρ`: 密度行列。
  * `dρ`: 推定される未知のパラメータに関する密度行列の微分。例えば、drho[1] は最初のパラメータに関する微分ベクトルです。
  * `rep`: RLD演算子の表現。オプションは「original」（デフォルト）と「eigen」です。
  * `eps`: マシンイプシロン。
