```
SLD(ρ::Matrix{T}, dρ::Vector{Matrix{T}}; rep="original", eps=GLOBAL_EPS) where {T<:Complex}
```

対称対数微分（SLD）を計算します。SLD演算子 $L_a$ は次のように定義されます：$\partial_{a}\rho=\frac{1}{2}(\rho L_{a}+L_{a}\rho)$、ここで $\rho$ はパラメータ化された密度行列です。

  * `ρ`: 密度行列。
  * `dρ`: 推定される未知のパラメータに関する密度行列の微分。例えば、drho[1] は最初のパラメータに関する微分ベクトルです。
  * `rep`: SLD演算子の表現。オプションは「original」（デフォルト）と「eigen」です。
  * `eps`: マシンイプシロン。
