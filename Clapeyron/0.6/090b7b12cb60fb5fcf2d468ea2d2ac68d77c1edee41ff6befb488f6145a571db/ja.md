```
GERG2008::MultiFluid

GERG2008(components;
        Rgas = 8.314472,
        reference_state = nothing,
        verbose = false)
```

## 入力パラメータ

なし

## 説明

GERG-2008天然ガスおよびその他の混合物のための広範囲状態方程式。21の化合物に対して有効です（`Clapeyron.GERG2008_names`）。

```

a = a⁰ + aʳ

a⁰ = ∑xᵢ(a⁰ᵢ(τᵢ,δᵢ) + ln(xᵢ))
δᵢ = ρ/ρcᵢ
τᵢ = Tcᵢ/T
a⁰ᵢ = ln(δᵢ) + R∗/R[n⁰ᵢ₋₁ + n⁰ᵢ₋₂τᵢ + n⁰ᵢ₋₃ln(τᵢ) + ∑n⁰ᵢ₋ₖln(abs(sinh(ϑ₀ᵢ₋ₖτᵢ))) + ∑n⁰ᵢ₋ₖln(cosh(ϑ₀ᵢ₋ₖτᵢ))]
R∗ = 8.314510
R = 8.314472

τ = Tᵣ/T
δ = ρ/ρᵣ
(1/ρᵣ) = ∑∑xᵢxⱼβᵥ₋ᵢⱼγᵥ₋ᵢⱼ[(xᵢ+xⱼ)/(xᵢβᵥ₋ᵢⱼ^2 + xⱼ)]•1/8(1/∛ρcᵢ + 1/∛ρcⱼ)^2
Tᵣ = ∑∑xᵢxⱼβₜ₋ᵢⱼγₜ₋ᵢⱼ[(xᵢ+xⱼ)/(xᵢβₜ₋ᵢⱼ^2 + xⱼ)]•√(TcᵢTcⱼ)
aʳ = ∑xᵢaᵣᵢ(τ,δ) + ∑∑xᵢxⱼFᵢⱼaʳᵢⱼ(τ,δ)
aʳᵢ = ∑nᵢ₋ₖδ^(dᵢ₋ₖ)τ^(tᵢ₋ₖ)  + ∑nᵢ₋ₖδ^(dᵢ₋ₖ)τ^(tᵢ₋ₖ)exp(-δ^cᵢ₋ₖ)
aʳᵢⱼ = ∑nᵢⱼ₋ₖδ^(dᵢⱼ₋ₖ)τ^(tᵢⱼ₋ₖ)  + ∑nᵢⱼ₋ₖδ^(dᵢⱼ₋ₖ)τ^(tᵢⱼ₋ₖ)exp(ηᵢⱼ₋ₖ(δ-εᵢⱼ₋ₖ)^2 + βᵢⱼ₋ₖ(δ-γᵢⱼ₋ₖ))
```

## 参考文献

1. Kunz, O., & Wagner, W. (2012). The GERG-2008 wide-range equation of state for natural gases and other mixtures: An expansion of GERG-2004. Journal of Chemical and Engineering Data, 57(11), 3032–3091. [doi:10.1021/je300655b](https://doi.org/10.1021/je300655b)
