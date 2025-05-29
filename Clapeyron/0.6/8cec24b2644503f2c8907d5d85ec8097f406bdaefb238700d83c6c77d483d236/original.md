```
PropaneRef <: EmpiricHelmholtzModel
PropaneRef()
```

## Input parameters

None

## Description

Propane Reference Equation of State

```
δ = ρ/ρc
τ = T/Tc
a⁰(δ,τ) = log(δ) + n⁰₁ + n⁰₂τ + n⁰₃log(τ) + ∑n⁰ᵢ(1-exp(-γ⁰ᵢτ)), i ∈ 4:7
aʳ(δ,τ)  = aʳ₁+ aʳ₂ + aʳ₃
aʳ₁(δ,τ)  = ∑nᵢδ^(dᵢ)τ^(tᵢ), i ∈ 1:5
aʳ₂(δ,τ)  = ∑nᵢexp(-δ^cᵢ)δ^(dᵢ)τ^(tᵢ), i ∈ 6:11
aʳ₃(δ,τ)  = ∑nᵢexp(-ηᵢ(δ - εᵢ)^2 - βᵢ(τ - γᵢ)^2)δ^(dᵢ)τ^(tᵢ), i ∈ 12:18

```

parameters  `n⁰`,`γ⁰`,`n`,`t`,`d`,`c`,`η`,`β`,`γ`,`ε` where obtained via fitting.

## References

1. Lemmon, E. W., McLinden, M. O., & Wagner, W. (2009). Thermodynamic properties of propane. III. A reference equation of state for temperatures from the melting line to 650 K and pressures up to 1000 MPa. Journal of Chemical and Engineering Data, 54(12), 3141–3180. [doi:10.1021/je900217v](https://doi.org/10.1021/je900217v)
