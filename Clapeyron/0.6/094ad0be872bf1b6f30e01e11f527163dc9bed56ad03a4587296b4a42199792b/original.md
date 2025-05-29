```
lambda_LorentzBerthelot(λ::ClapeyronParam,k = 3)::PairParam
```

Combining rule for a single or pair parameter. returns a pair parameter with non diagonal entries equal to:

```
λᵢⱼ = k + √((λᵢᵢ - k)(λⱼⱼ - k))
```

with `k = 0` the definition is reduced to a simple geometric mean:

```
ϵᵢⱼ = √(ϵᵢϵⱼ)
```

Ignores non-diagonal entries already set.

If a Single Parameter is passed as input, it will be converted to a Pair Parameter with `λᵢᵢ = λᵢ`.
