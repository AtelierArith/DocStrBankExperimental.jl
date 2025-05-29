```
Ammonia2023 <: EmpiricHelmholtzModel
Ammonia2023()
```

## Input parameters

None

## Description

Ammonia Reference Equation of State (2023)

```
δ = ρ/ρc
τ = T/Tc
a⁰(δ,τ) = log(δ) + n⁰₁ + n⁰₂τ + n⁰₃log(τ) + ∑n⁰ᵢ(1-exp(-γ⁰ᵢτ)), i ∈ 4:7
aʳ(δ,τ)  = aʳ₁+ aʳ₂ + aʳ₃
aʳ₁(δ,τ)  = ∑nᵢδ^(dᵢ)τ^(tᵢ), i ∈ 1:5
aʳ₂(δ,τ)  = ∑nᵢexp(-δ^cᵢ)δ^(dᵢ)τ^(tᵢ), i ∈ 6:8
aʳ₃(δ,τ)  = ∑nᵢexp(-ηᵢ(δ - εᵢ)^2 - βᵢ(τ - γᵢ)^2)δ^(dᵢ)τ^(tᵢ), i ∈ 9:18
aʳ₃(δ,τ)  = ∑nᵢexp(-ηᵢ(δ - εᵢ)^2 - 1/(βᵢ*(τ -γᵢ)^2 + bᵢ))δ^(dᵢ)τ^(tᵢ), i ∈ 19:20

```

parameters  `n⁰`,`γ⁰`,`n`,`t`,`d`,`c`,`η`,`β`,`γ`,`ε` where obtained via fitting.

## References

1. Gao, K., Wu, J., Bell, I. H., Harvey, A. H., & Lemmon, E. W. (2023). A reference equation of state with an associating term for the thermodynamic properties of ammonia. Journal of Physical and Chemical Reference Data, 52(1), 013102. [doi:10.1063/5.0128269](https://doi.org/10.1063/5.0128269)
