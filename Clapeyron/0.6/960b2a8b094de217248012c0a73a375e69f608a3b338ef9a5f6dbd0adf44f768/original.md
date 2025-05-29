```
epsilon_LorentzBerthelot(ϵ::SingleOrPair,k::PairParam)::PairParam
epsilon_LorentzBerthelot(ϵ::SingleOrPair)::PairParam
```

Combining rule for a single or pair parameter. returns a pair parameter with non diagonal entries equal to:

```
ϵᵢⱼ = (1 - kᵢⱼ)*√(ϵᵢϵⱼ)
```

If `kᵢⱼ` is not defined, the definition is reduced to a simple geometric mean:

```
ϵᵢⱼ = √(ϵᵢϵⱼ)
```

Ignores non-diagonal entries already set.

If a Single Parameter is passed as input, it will be converted to a Pair Parameter with `ϵᵢᵢ = ϵᵢ`.
