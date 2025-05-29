```
lambda_squarewell(λ::SingleOrPair,σ::PairParam)::PairParam
```

Combining rule for a single or pair parameter. returns a pair parameter with non diagonal entries equal to:

```
λᵢⱼ = (σᵢᵢλᵢᵢ + σⱼⱼλⱼⱼ)/(σᵢᵢ + σⱼⱼ)
```

Ignores non-diagonal entries already set.

If a Single Parameter is passed as input, it will be converted to a Pair Parameter with `λᵢᵢ = λᵢ`.
