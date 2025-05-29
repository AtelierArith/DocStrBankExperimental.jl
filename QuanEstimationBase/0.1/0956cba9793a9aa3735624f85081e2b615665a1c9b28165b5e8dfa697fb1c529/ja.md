```
LLD(ρ::Matrix{T}, dρ::Vector{Matrix{T}}; rep="original", eps=GLOBAL_EPS) where {T<:Complex}
```

左対数微分（LLD）を計算します。LLD演算子は$\partial_{a}\rho=\mathcal{R}_a^{\dagger}\rho$として定義され、ここでρはパラメータ化された密度行列です。

  * `ρ`: 密度行列。
  * `dρ`: 推定される未知のパラメータに関する密度行列の微分。例えば、drho[1]は最初のパラメータに関する微分ベクトルです。
  * `rep`: LLD演算子の表現。オプションは「original」（デフォルト）と「eigen」です。
  * `eps`: マシンエプシロン。

```
