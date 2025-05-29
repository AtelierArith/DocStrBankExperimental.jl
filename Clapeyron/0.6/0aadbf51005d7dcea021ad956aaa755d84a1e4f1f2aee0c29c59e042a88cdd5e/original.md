```
epsilon_HudsenMcCoubrey(ϵ::SingleOrPair,σ::PairParam)::PairParam
epsilon_HudsenMcCoubrey(ϵ::SingleOrPair)::PairParam
```

Combining rule for a single or pair parameter. returns a pair parameter with non diagonal entries equal to:

```
ϵᵢⱼ = √(ϵᵢϵⱼ)*(σᵢᵢ^3 * σⱼⱼ^3)/σᵢⱼ^6 
```

If `σᵢⱼ` is not defined, the definition is reduced to a simple geometric mean:

```
ϵᵢⱼ = √(ϵᵢϵⱼ)
```

Ignores non-diagonal entries already set.

If a Single Parameter is passed as input, it will be converted to a Pair Parameter with `ϵᵢᵢ = ϵᵢ`.
