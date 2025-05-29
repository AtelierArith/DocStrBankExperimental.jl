```
kij_mix(f,p::ClapeyronParam,k::PairParam)::PairParam
kij_mix(f,p::ClapeyronParam)::PairParam
```

General combining rule for pair parameter with a `kᵢⱼ` interaction parameter. returns a pair parameter with non diagonal entries equal to:

```
pᵢⱼ = f(pᵢ,pⱼ,kᵢⱼ)
```

Where `f` is a 'combining' function that follows the rules:

```
f(pᵢ,pⱼ,0) = f(pⱼ,pᵢ,0)
f(pᵢ,pᵢ,0) = pᵢ
```

and `k` must follow:

```
kᵢᵢ = 0 
```

Ignores non-diagonal entries already set.

If a Single Parameter is passed as input, it will be converted to a Pair Parameter with `pᵢᵢ = pᵢ`.
