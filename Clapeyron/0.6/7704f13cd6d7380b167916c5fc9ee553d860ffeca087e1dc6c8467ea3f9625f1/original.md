```
IAPWS95 <: EmpiricHelmholtzModel
IAPWS95()
```

## Input parameters

None

## Description

IAPWS95 (International Association for the Properties of Water and Steam) Pure water Model, 2018 update.

```
δ = ρ/ρc
τ = T/Tc
a⁰(δ,τ) = log(δ) + n⁰₁ + n⁰₂τ + n⁰₃log(τ) + ∑n⁰ᵢ(1-exp(-γ⁰ᵢτ)), i ∈ 4:8
aʳ(δ,τ)  = aʳ₁+ aʳ₂ + aʳ₃ + aʳ₄
aʳ₁(δ,τ)  = ∑nᵢδ^(dᵢ)τ^(tᵢ), i ∈ 1:7
aʳ₂(δ,τ)  = ∑nᵢexp(-δ^cᵢ)δ^(dᵢ)τ^(tᵢ), i ∈ 8:51
aʳ₃(δ,τ)  = ∑nᵢexp(-αᵢ(δ - εᵢ)^2 - βᵢ(τ - γᵢ)^2)δ^(dᵢ)τ^(tᵢ), i ∈ 52:54
aʳ₄(δ,τ) = ∑nᵢδΨΔ^(bᵢ), i ∈ 55:56
Δ = θ^2 + Bᵢ[(δ - 1)^2]^aᵢ
θ = (1 - τ) + Aᵢ[(δ - 1)^2]^(1/2βᵢ)
Ψ = exp(-Cᵢ(δ - 1)^2 - Dᵢ(τ - 1)^2)
```

parameters `n⁰`,`γ⁰`,`n`,`t`,`d`,`c`,`α`,`β`,`γ`,`ε`,`A`,`B`,`C`,`D` where obtained via fitting.

## References

1. Wagner, W., & Pruß, A. (2002). The IAPWS formulation 1995 for the thermodynamic properties of ordinary water substance for general and scientific use. Journal of physical and chemical reference data, 31(2), 387–535. [doi:10.1063/1.1461829](https://doi.org/10.1063/1.1461829)
2. IAPWS R6-95 (2018). Revised Release on the IAPWS Formulation 1995 for the Thermodynamic Properties of Ordinary Water Substance for General and Scientific Use
