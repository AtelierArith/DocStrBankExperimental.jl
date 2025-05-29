```
sigma_LorentzBerthelot(σ::SingleOrPair,ζ::PairParam)::PairParam
sigma_LorentzBerthelot(σ::SingleOrPair)::PairParam
```

Combining rule for a single or pair parameter. returns a pair parameter with non diagonal entries equal to:

```
σᵢⱼ = (1 - ζᵢⱼ)*(σᵢ + σⱼ)/2
```

If `ζᵢⱼ` is not defined, the definition is reduced to a simple arithmetic mean:

```
σᵢⱼ = (σᵢ + σⱼ)/2
```

Ignores non-diagonal entries already set.

If a Single Parameter is passed as input, it will be converted to a Pair Parameter with `σᵢᵢ = σᵢ`.
