EmpiricDeparture <: MultiFluidDepartureModel     EmpiricDeparture(components;     userlocations = String[],     verbose = false)

## Input parameters

none

  * `F`: Pair Parameter (`Float64`) - binary interaction parameter (no units)
  * `parameters`: Pair Parameter (`String`) - JSON data containing the departure terms for the binary pair

## Description

Departure that uses empiric departure functions:

```
aᵣ = ∑xᵢaᵣᵢ(δ,τ) + Δa
Δa = ∑xᵢxⱼFᵢⱼaᵣᵢⱼ(δ,τ)

aᵣᵢⱼ = ∑nᵢⱼ₋ₖδ^(dᵢⱼ₋ₖ)*τ^(tᵢⱼ₋ₖ) +
    ∑nᵢⱼ₋ₖδ^(dᵢⱼ₋ₖ)τ^(tᵢⱼ₋ₖ)*exp(-gᵢⱼ₋ₖδ^lᵢⱼ₋ₖ) +
    ∑nᵢⱼ₋ₖδ^(dᵢⱼ₋ₖ)τ^(tᵢⱼ₋ₖ)*exp(ηᵢⱼ₋ₖ(δ-εᵢⱼ₋ₖ)^2 + βᵢⱼ₋ₖ(τ-γᵢⱼ₋ₖ)^2)

```
