EmpiricDeparture <: MultiFluidDepartureModel     EmpiricDeparture(components;     userlocations = String[],     verbose = false)

## 入力パラメータ

なし

  * `F`: ペアパラメータ (`Float64`) - バイナリ相互作用パラメータ（単位なし）
  * `parameters`: ペアパラメータ (`String`) - バイナリペアの出発項を含むJSONデータ

## 説明

経験的出発関数を使用する出発：

```
aᵣ = ∑xᵢaᵣᵢ(δ,τ) + Δa
Δa = ∑xᵢxⱼFᵢⱼaᵣᵢⱼ(δ,τ)

aᵣᵢⱼ = ∑nᵢⱼ₋ₖδ^(dᵢⱼ₋ₖ)*τ^(tᵢⱼ₋ₖ) +
    ∑nᵢⱼ₋ₖδ^(dᵢⱼ₋ₖ)τ^(tᵢⱼ₋ₖ)*exp(-gᵢⱼ₋ₖδ^lᵢⱼ₋ₖ) +
    ∑nᵢⱼ₋ₖδ^(dᵢⱼ₋ₖ)τ^(tᵢⱼ₋ₖ)*exp(ηᵢⱼ₋ₖ(δ-εᵢⱼ₋ₖ)^2 + βᵢⱼ₋ₖ(τ-γᵢⱼ₋ₖ)^2)

```
