```
LJRef <: EmpiricHelmholtzModel
LJRef(components;
userlocations = String[],
verbose = false)
```

## Input parameters

  * `sigma`: Single Parameter (`Float64`) - particle size [Å]
  * `epsilon`: Single Parameter (`Float64`) - dispersion energy [`K`]
  * `Mw`: Single Parameter (`Float64`) - Molecular Weight `[g/mol]`
  * `k`: Pair Parameter (`Float64`) (optional) - `sigma` mixing coefficient

## Model Parameters

  * `sigma`: Pair Parameter (`Float64`) - particle size [m]
  * `epsilon`: Pair Parameter (`Float64`) - dispersion energy [`K`]
  * `Mw`: Single Parameter (`Float64`) - Molecular Weight `[g/mol]`

## Description

Lennard-Jones Reference equation of state. valid from 0.5 < T/Tc < 7 and pressures up to p/pc = 500.

```
σᵢⱼ = (σᵢ + σⱼ)/2
ϵᵢⱼ = (1-kᵢⱼ)√(ϵⱼϵⱼ)
σ^3 = Σxᵢxⱼσᵢⱼ^3
ϵ = Σxᵢxⱼϵᵢⱼσᵢⱼ^3/σ^3
τᵢ = 1.32ϵᵢ/T
δᵢ = n(Nₐσᵢ^3)/0.31V
a⁰ᵢ(δ,τ) = log(δᵢ) + 1.5log(τᵢ) - 1.515151515τᵢ + 6.262265814
a⁰(δ,τ,z) = ∑xᵢ(a⁰ᵢ + log(xᵢ))
τ = 1.32ϵ/T
δ = n(Nₐσ^3)/0.31V
aʳ(δ,τ)  = aʳ₁+ aʳ₂ + aʳ₃ + aʳ₄
aʳ₁(δ,τ)  = ∑nᵢδ^(dᵢ)τ^(tᵢ), i ∈ 1:6
aʳ₂(δ,τ)  = ∑nᵢexp(-δ^cᵢ)δ^(dᵢ)τ^(tᵢ), i ∈ 7:12
aʳ₃(δ,τ)  = ∑nᵢexp(-ηᵢ(δ - εᵢ)^2 - βᵢ(τ - γᵢ)^2)δ^(dᵢ)τ^(tᵢ), i ∈ 13:23
```

parameters `n`,`t`,`d`,`c`,`η`,`β`,`γ`,`ε` where obtained via fitting.

!!! warning "Multiple component warning"
    The original model was done with only one component in mind. to support multiple components, a VDW 1-fluid mixing rule (shown above) is implemented, but it is not tested.


## References

1. Thol, M., Rutkai, G., Köster, A., Lustig, R., Span, R., & Vrabec, J. (2016). Equation of state for the Lennard-Jones fluid. Journal of physical and chemical reference data, 45(2), 023101. [doi:10.1063/1.4945000](https://doi.org/10.1063/1.4945000)
